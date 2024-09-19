# catalogo
de moda
<?php
session_start();
if (!isset($_SESSION['user'])) {
    header("Location: login.php");
    exit;
}

include 'app/Conect.php';
include 'app/Acciones.php';

$acciones = new Acciones($Conecta);
$moda = $acciones->mostrarModa();
?>

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Catálogo de Moda</title>
</head>
<body>
    <h2>Catálogo de Moda</h2>
    <table border="1">
        <thead>
            <tr>
                <th>Nombre</th>
                <th>Categoría</th>
                <th>Precio</th>
                <th>Descripción</th>
            </tr>
        </thead>
        <tbody>
            <?php foreach ($moda as $articulo): ?>
                <tr>
                    <td><?php echo htmlspecialchars($articulo['nombre']); ?></td>
                    <td><?php echo htmlspecialchars($articulo['categoria']); ?></td>
                    <td><?php echo htmlspecialchars($articulo['precio']); ?></td>
                    <td><?php echo htmlspecialchars($articulo['descripcion']); ?></td>
                </tr>
            <?php endforeach; ?>
        </tbody>
    </table>
    <a href="catalogo.php?logout=true">Cerrar sesión</a>
</body>
</html>
