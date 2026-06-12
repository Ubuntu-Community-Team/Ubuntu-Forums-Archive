---
title: "mysql re instalar"
date: 2020-08-25
forum: Centroamerica Team
---

### Post by esteban78 on 2020-08-25
Buenas soy muy nuevo en esto . pero lo necesito, 
instale mysql en ubuntu 20.04 quise acceder y no recuedo el passs de root. entonces segui tutoriales para recuperar contaseña, al no funcionar desidi  desintalar mysql para volver a instalarlo  limpio. pero nada no me deja me dice que ya existe pero cuando intento acceder por consola me dice que no . que info deberia poner aqui para que algien me ayude . ? algun log o las respuestas que me da la consola ? gracias

---

### Post by danielperez81 on 2020-10-24
[FONT=arial]Hola Esteban

Para remover completamente MySQL de tu sistema, utiliza el siguiente comando:

 sudo apt-get purge mariadb-*

Si no recuerdas la contraseña de root, no puedes utilizar ningún servicio que requiere root, salvo que seas superusuario. Para convertir tu usuario actual podrías convertir tu usuario en superusuario utilizando el siguiente comando:

usermod -aG sudo juan

En donde suponemos que "juan" es tu nombre de usuario. Una vez que eres superusuario, vuelve a intentar si te permite instalar MySQL (MariaDB)

Fuente: [/FONT][https://bitcu.co/creacion-de-usuarios-grupos-y-superusuarios-en-linux/](https://bitcu.co/creacion-de-usuarios-grupos-y-superusuarios-en-linux/)

[FONT=arial]En caso de no permitirte cambiar tu superusuario, podrías intentar modificar el archivo /etc/shadow, que es el lugar en donde se almacenan las contraseñas de inicio, desafortunadamente está cifrado el archivo. 

La sintaxis del archivo es $id$salt$hash, el cual te podría dar una idea de cómo está cifrado y con qué algoritmo, pero salvo que tu contraseña sea corta, es un proceso realmente largo por medio de fuerza bruta.

[/FONT][FONT=arial]Saludos [/FONT]):P[FONT=arial]

[/FONT]

---

