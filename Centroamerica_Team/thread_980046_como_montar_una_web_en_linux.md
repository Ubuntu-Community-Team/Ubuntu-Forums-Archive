---
title: "como montar una web en linux"
date: 2008-11-12
forum: Centroamerica Team
---

### Post by yariel on 2008-11-12
si buenas a todos es que tengo que montar un webserver para tener una pagina web  en una computdora que tiene linux ubuntu si alguien me puede ayudar se le agradeceria

---

### Post by eivar on 2008-11-12
Hola yariel se un poco más específico por favor y con mucho gusto te podemos ayudar.
¿Deseas instalar apache, mysql y php?

Lo más simple es buscar en synaptic apache, mysql y php e instalarlos, el synaptic te dirá las dependencias apropiadas que se instalaran y listo.

Te dejo un par de guías que te pueden servir:
[http://glanzas.blogia.com/2007/090701--howto-como-instalar-un-servidor-lamp-en-ubuntu-feisty-en-5-sencillos-pasos..php](http://glanzas.blogia.com/2007/090701--howto-como-instalar-un-servidor-lamp-en-ubuntu-feisty-en-5-sencillos-pasos..php)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by greer on 2008-11-12
hermano no ahi problema mira si ya tienes instalado ubuntu Desktop que es la vercion de escritorio y no la de server que es por terminal no ahi problema, haz lo siguiente:

vas a synaptic y no busques nada que ahi una opcion que te ayuda para ese fin...

Abres Synaptic y vas a la barra de arriba la opcion que dice **EDIT** Entre File y Package, bueno le das clik y te vas a la Penultima Opcion que dice:

**Mark Packages by Task** le das clik y le pones ganchito a **LAMP Server**

con eso ya tienes todo listo :)

---

### Post by yariel on 2008-11-13
gracias por su ayuda lo voy a hacer ahora en la noche yaque tengo la computadora en mi casa.


gracias por la atencion prestada

---

### Post by black_master on 2008-11-13
yariel, escribi un tutorial sobre eso, visita mi web:
[http://www.softwarelibrelatino.co.cc/?p=48]("http://www.softwarelibrelatino.co.cc/?p=48")
miralo, si necesitas ayuda con un cms o algo, escribeme en el foro o en el irc :D 
un saludo

---

### Post by srlinux on 2008-11-15
Instalar LAMP (Linux Apache MySQL PHP) en tu máquina conUbuntu no podría ser más fácil.
Con esta guía aprenderás cómo hacerlo en unos cuantos minutos. El procedimiento se divide en tres partes, instalar y minutos.El procedimiento se divide en tres partes, instalar y probar Apache, después PHP y finalmente MySQL..
Comencemos con Apache

En tu terminal (Aplicaciones &#8594; Accesorios &#8594; Terminal) teclea:

1- sudo apt-get install apache2

Listo, ya tienes instalado Apache 2 en tu máquina.

Por lo regular después de la instalación el servidor web será
iniciado automáticamente, pero si necesitas iniciarlo de
manera manual teclea esto en tu terminal:

sudo /etc/init.d/apache2 start

Si por alguna razón necesitas detener el servicio, escribe en tu
terminal:

sudo /etc/init.d/apache2 stop

El directorio donde se almacenan tus documentos web es:
/var/www

Si todo resultó bien, debes ver una página web ordinaria al
escribir [http://localhost](http://localhost) en la barra de direcciones de tu
navegador.
Hemos terminado con Apache, ahora a la conquista de PHP

Escribe en tu terminal:

sudo apt-get install php5 libapache2-mod-php5

Reinicia Apache con:

sudo /etc/init.d/apache2 restart

Terminamos con PHP :D

Para probar que se haya instalado correctamente vamos a
crear un pequeño script en PHP. Escribe en tu terminal:

sudo gedit /var/www/test.php

Ponle este contenido y guárdalo:


phpinfo();

?>
phpinfo();

?>

Para ejecutar el script ve a esta dirección: [http://localhost](http://localhost)
/test.php — debes ver una página con información sobre tu
instalación de PHP.
66% concluido, continuemos con MySQL

De nuevo, escribe en tu terminal

sudo apt-get install mysql-server

phpMyAdmin es un administrador gráfico para MySQL, yo no lo uso pero es mas fasil asi XD Para instalarlo teclea en tu terminal:

sudo apt-get install phpmyadmin

Para acceder a él visita: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
gd library


Hay un problema cuando se instala desde los repositorios,
después de instalarlo hay que hacer un enlace simbólico desde
/usr/share/phpmyadmin hacia /var/www/phpmyadmin
sudo ln -s /usr/share/phpmyadmin /var/www/

Si deseas soporte para generación y manipulación de gráficos
en PHP, escribe en tu terminal:

sudo apt-get install php5-gd

SSL en Apache 2

Para activar el módulo SSL (Secure Socket Layer) en Apache 2,
ingresa en tu terminal:

sudo a2enmod ssl

Reinicia Apache con:

sudo /etc/init.d/apache2 restart

Puedes descargar el pdf aqui [Server Lamp.pdf]("http://www.mediafire.com/?z2jbwyytm52")

para mas detalles visita mi foro [http://srinuxubuntu.homelinux.com/foro/viewtopic.php?f=4&t=25&sid=963536a9b0f74a6ab0b9b2e4b119dc71](http://srinuxubuntu.homelinux.com/foro/viewtopic.php?f=4&t=25&sid=963536a9b0f74a6ab0b9b2e4b119dc71)

Saludos y suerte

---

### Post by yariel on 2008-11-20
gracias por todo me funciono, esta pagina es lo maximo gracias.

---

### Post by yariel on 2009-03-14
buenos dias a todos si esque soy nuevo en esto de linux y necesito montar un servidor ftp si alguien me puede decir que programa puedeo usar o como debo hacer es que cuando trato de busar todo lo que me sale esta en windows

---

### Post by eivar on 2009-03-16
Hola Yariel, por favor busca en tu gestor de paquetes (synaptic si usas gnome), puedes probar buscar con el termino "ftp" (sin las comillas) y encontraras muchos programas relacionados.

Puedes buscar también en google "ftp+server+linux" sin las comillas.

Una cosa más, ya que esta pregunta no está relacionada con el post anterior (un web server en linux) es mejor colocarla en un post nuevo, ya para este ni modo pero para la proxima ya sabes si tienes una pregunta nueva en un post nuevo ya así llevamos esto con más orden y adicional es más simple que alguien te pueda dar una respuesta a tu pregunta.

Saludos.

---

### Post by greer on 2009-03-16
un servidor ftp... mmm ok instalate este programa:

sudo apt-get install **vsftpd**

y listo ya tendras un servidor ftp corriendo. y para modificar una que otra opcion vas a su archivo de configuracion, ubicado en **/etc/vsftpd.conf**

los usuarios los agregas usando:

**adduser**

osea, creando usuarios en el sistema...

---

### Post by mayeco on 2009-03-17
> **black_master said:**
> yariel, escribi un tutorial sobre eso, visita mi web:
[http://www.softwarelibrelatino.co.cc/?p=48]("http://www.softwarelibrelatino.co.cc/?p=48")
miralo, si necesitas ayuda con un cms o algo, escribeme en el foro o en el irc :D 
un saludo

ese URL no funciona lo mejor es siempre escribir la respuesta aquí mismo sin dar referencia a sitios(nada mas para obtener visitas).

---

### Post by srlinux on 2009-04-15
Hola para configurar un server fto aqui te dejo un pequeño tuto bien explicado q hice 

Guia para configurar un server FTP en ubuntu de una forma segura y en muy pocos pasos

Bien procedamos a su instalación y configuración en nuestro Ubuntu, previamente a ello debemos asegurarnos que nuestro puerto 21, esté abierto.

```
sudo apt-get install vsftpd
```

Luego que ya lo tenemos instalado vamos a proceder a configurar nuestro servidor, aplicando las reglas al archivo **vsftpd.conf**

descarga configuracion [aqui]("http://supremoteam.comuf.com/descargas/config")

ya que tenemos configurado nuestro vsftpd reiniciamos el ftp

```
sudo /etc/init.d/vsftpd restart
```

crear usuarios ftp

```
sudo useradd -d /var/www -s/bin/bash nombre_del_usuario
```

creamos su password

```
sudo passwd nombre_del_usuario
```

Con ello habremos creado el usuario usuario1, asignado su carpeta personal y asignado también una password.

permiso para la carpeta del usuario

```
sudo chmod 777 /var/www
```

despues creamos un shell fantasma

```
sudo mkdir /bin/ftp
```

Editamos el fichero **/etc/shells** y la añadimos en la ultima línea **/bin/ftp**

```
sudo gedit /etc/shells
```

agregamos al final

```
/bin/ftp
```

luego editamos el **passwd**

```
sudo gedit /etc/passwd
```

y agregamos al final donde están definidos los usuarios que hemos creado **/bin/ftp**

```
user:x:1003:1003::/var/www:/bin/ftp 
```

si queremos eliminar un usuario de nuestro ftp abrimos ```
passwd
```

y borramos el usuario que queramos tambien se puede borrar desde Sistema &#8594; Administración &#8594; Usuarios y Grupos


Fuente: [http://srinuxubuntu.homelinux.com/index.php/servidor-ftp-con-vsftpd-en-ubuntu/](http://srinuxubuntu.homelinux.com/index.php/servidor-ftp-con-vsftpd-en-ubuntu/)

Seguridad:[http://supremoteam.comuf.com/index.php/Maxima_seguridad_para_tu_server_lamp](http://supremoteam.comuf.com/index.php/Maxima_seguridad_para_tu_server_lamp)

suerte cualquier duda aqui estare pendiente :D

---

### Post by mayeco on 2009-04-22
> **black_master said:**
> yariel, escribi un tutorial sobre eso, visita mi web:
[http://www.softwarelibrelatino.co.cc/?p=48]("http://www.softwarelibrelatino.co.cc/?p=48")
miralo, si necesitas ayuda con un cms o algo, escribeme en el foro o en el irc :D 
un saludo

por favor envia el tutorial en el mismo foro no envies enlaces a otros sitios.

---

