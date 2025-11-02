1. Título

Práctica de creación de contenedores MySQL y phpMyAdmin con Docker

2. Tiempo de duración

Duración aproximada: 30 minutos

3. Fundamentos

Docker es una herramienta que permite crear, desplegar y ejecutar aplicaciones usando contenedores. Los contenedores son entornos ligeros y portables que incluyen todo lo necesario para que la aplicación funcione, como librerías, dependencias y archivos de configuración. Esto significa que la aplicación se puede ejecutar igual en cualquier equipo que tenga Docker instalado, sin preocuparse de conflictos con otras aplicaciones o sistemas operativos.

Un contenedor se diferencia de una máquina virtual porque no necesita un sistema operativo completo, solo comparte el kernel del sistema anfitrión, lo que hace que sea mucho más eficiente en términos de recursos. Además, Docker permite crear redes internas para que los contenedores puedan comunicarse entre sí de manera segura. Esto es útil, por ejemplo, para separar la base de datos de la aplicación web y mantener un entorno más organizado y seguro.

En esta práctica se van a crear dos contenedores: uno para MySQL y otro para phpMyAdmin. MySQL es un sistema de gestión de bases de datos relacional muy popular, mientras que phpMyAdmin es una herramienta web que permite administrar MySQL desde un navegador. Al crear ambos contenedores y conectarlos a una red personalizada en Docker, podemos administrar la base de datos de manera más sencilla y probar la comunicación entre contenedores.

Las redes de Docker permiten que los contenedores se identifiquen por nombres y puedan enviar y recibir datos entre sí. Por ejemplo, si conectamos phpMyAdmin a la red que tiene MySQL, podremos acceder a la base de datos usando el nombre del contenedor MySQL sin necesidad de usar direcciones IP complicadas.

Figura 3-1. Esquema de contenedores conectados mediante red Docker


4. Conocimientos previos

Para realizar esta práctica el estudiante necesita manejar los siguientes conceptos:

Comandos básicos de Docker: docker run, docker ps, docker network create.

Concepto de contenedores y su diferencia con máquinas virtuales.

Manejo de navegadores web para acceder a interfaces como phpMyAdmin.

Conocimientos básicos de bases de datos MySQL: creación de bases de datos y usuarios.

Conceptos de redes en Docker para permitir comunicación entre contenedores.

5. Objetivos a alcanzar

Implementar contenedores para MySQL y phpMyAdmin usando Docker.

Manipular archivos de configuración para establecer credenciales y conexiones.

Configurar una red personalizada que permita la comunicación entre ambos contenedores.

Crear una base de datos de prueba desde phpMyAdmin.

6. Equipo necesario

Computador con sistema operativo Windows/Linux/Mac

Cuenta en Docker Hub (opcional para descargar imágenes)

Docker Desktop versión 4.x o superior

Conexión a Internet para descargar imágenes oficiales de MySQL y phpMyAdmin

Navegador web moderno (Chrome, Firefox, Edge)

7. Material de apoyo

Documentación oficial de Docker: https://docs.docker.com

Guía de asignatura de contenedores

Cheat sheet de Linux y comandos básicos de Docker

Tutoriales de MySQL y phpMyAdmin

8. Procedimiento

Paso 1: Crear red personalizada en Docker

docker network create red_mysql_phpmyadmin


Esto permite que los contenedores se comuniquen usando nombres en vez de IP.

Paso 2: Crear contenedor de MySQL

docker run -d --name mysql-server --network red_mysql_phpmyadmin -e MYSQL_ROOT_PASSWORD=mi_contraseña -e MYSQL_DATABASE=prueba mysql:8


Se define la contraseña del root y una base de datos de prueba.

Paso 3: Crear contenedor de phpMyAdmin

docker run -d --name phpmyadmin --network red_mysql_phpmyadmin -e PMA_HOST=mysql-server -p 8080:80 phpmyadmin/phpmyadmin


Se indica que phpMyAdmin se conectará al contenedor MySQL llamado mysql-server.

Paso 4: Verificar contenedores en ejecución

docker ps


Se debe ver ambos contenedores en estado Up.

Paso 5: Acceder a phpMyAdmin desde el navegador
Abrir http://localhost:8080 e iniciar sesión con usuario root y la contraseña configurada.

Paso 6: Crear base de datos de prueba desde phpMyAdmin

Hacer clic en "Nueva" y asignar un nombre, por ejemplo, bd_prueba.

Confirmar la creación y verificar que aparece en la lista de bases de datos.

9. Resultados esperados

Dos contenedores en ejecución: MySQL y phpMyAdmin.

Red Docker personalizada que permite comunicación entre los contenedores.

Acceso a phpMyAdmin mediante navegador web y posibilidad de administrar la base de datos MySQL.

Base de datos de prueba creada y visible desde phpMyAdmin.

10. Bibliografía

Merkel, D. (2014). Docker: Lightweight Linux Containers for Consistent Development and Deployment. Linux Journal.

Docker, Inc. (2023). Docker Documentation. Recuperado de https://docs.docker.com

MySQL. (2023). MySQL Reference Manual. Oracle Corporation. Recuperado de https://dev.mysql.com/doc/

phpMyAdmin. (2023). phpMyAdmin Documentation. Recuperado de https://www.phpmyadmin.net/docs/
