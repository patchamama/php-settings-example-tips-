# php-settings-example-tips-

Actualización a partir de video de midudev: https://www.youtube.com/watch?v=BcGAPkjt_IE

## Instrucciones de ejecución insteresantes desde línea de comando
```bash
# Instalación MacOsX (windows ver xampp o wampp)
brew install php

# Ver ayuda
php --help

# Ver versión instalada
php -v

# Ejecutar php con instrucciones
php -r "echo 'Hola mundo!'"

# Ejecutar script
php <script.php>

# Ejecutar un servidor web con php (sin necesidad de apache). Sí hay un index.php, se mostraría automáticamente en el navegador al visitar http://localhost:8080
php -S localhost:8080
```

## El lenguaje

```php
// Equivalente a <?php echo "Hola mundo"; ?>, es decir <?php con echo...
<?= "Hola mundo!"; ?>

// Para las variables se puede usar camelCase o snake_case, mejor camelCase

// Saber un tipo de dato y su valor (var_dump)
<?php
  $name = "Hola";
  $numero = 4;
  $isTrue = true;
  $age = 44;

 var_dump($name);    // string(4) Hola
 var_dump($numero);  // int(4)
 var_dump(isTrue);   // bool(true)

 // también se puede usar echo gettype(var)
 echo gettype($name);  // string
 is_string($name);     // true

 // typecasting. Se agrega el tipo entre paréntesis antes
 echo (bool) "Pepe"; // true
 echo (int) "Jose";  // 0

 // Imprimir valor de variables en string (debe de estar la string o variable entre comillas dobles)
 echo "$name tiene $age años";
 $output = "$name tiene $age años";
 echo $output;
 $output .= ", y está desempleado." //concatenación
?>

// Constantes (no hay que poner el símbolo de dólar antes
define('PI', 3.14)     // constante global
const NOMBRE = "Pablo" // constante local
<?= NOMBRE ?>

// Condición If (se puede usar "elseif" o "else if" 
if (cond1) {
} elseif (cond2) {
} else {
}

// Sí se usa de esta forma no se puede usar "else if"
<?php if (cond1) : ?>
  <h3>Ejemplo de código1</h3>
<?php elseif (cond2) : ?>
  <h3>Ejemplo de código2</h3>
<?php else : ?>
  <h3>Ejemplo de código3</h3>
<?php endif; ?>

// Ternearias
<?php
$age = 13;
$isOld = $age > 40;
$outputOld = $IsOld
  ? "Es viejo"
  : "Es jóven";
?>
<h2><?= $outputOld ?></h2>

// match como mejor alternativa a switch
<?php
$output = match($age) {
   0, 1, 2, 3                 => "es un bebé",
   4, 5, 6, 7, 8, 9, 10, 11   => "es un niño",
   12, 13, 14, 15, 16, 17, 18 => "es un adolescente",
   default                    => "es un adulto",
};

// aún mejor con match poniendo condiciones 
$output = match(true) {
  $age <= 3   => "es un bebé",
  $age <= 11  => "es un niño",
  $age <= 18  => "es un adolescente",
  default     => "es un adulto",
};

// Arrays
$example = array("Hola", 1, true)
$languagesProg = ["PHP", "Javascript", 1, 2]
$languagesProg[3] = "Java" // sustituye 2 por Java
$languagesProg[] = "TypeScript" // agrega al final typescript
<h3>El mejor lenguaje de programación es <?= $languagesProg[0] ?>.</h3>

// Iterar array
<ul>
  <?php foreach($languagesProg as $lang) : ?>
    <li><?= $lang ?></li>
  <?php endforeach; ?>
</ul>

// Iterar con índice
<ul>
  <?php foreach($languagesProg as $key => $lang) : ?>
    <li><?= $key . " " . $lang ?></li>
  <?php endforeach; ?>
</ul>

<?php
// array asociativo, similar a un diccionario
$person = [
  "name" => "miguel",
  "age"  => 42,
  "isDev" => true,
  "languages" => ["php", "javascript", "python"]
];
$person["name"] = "pedro";
$person["languages"][] = "java";

// Acceso a API
// Ver usando curl o get_file_content()
?>
```
