---
title: "inicio de Ubuntu"
date: 2018-10-10
forum: Centroamerica Team
---

### Post by rankapino on 2018-10-10
Hola,  
Tengo un ASUS GL752VW i7 de 16Gb, en el que instalé Ubuntu 17.10.  
Mi problema es que cada vez que enciendo el portátil, la pantalla de  inicio (donde pone Ubuntu y una barra de estado) se bloquea. Entonces  tengo que reiniciar y cuando me da las 3 opciones de arranque, le tengo  que pulsar la letra "e" para editar y detrás de "quiet splash" añadir  "nouveau.modeset=0". Después de añadir esto y pulsar F10, el ordenador  arranca normal. 

Pero es un engorro bastante jodido tener que hacerlo todos los días y ademas no me gusta tener que reiniciar el ordenador.  

Agradecería cualquier ayuda ya que llevo meses así y ya estoy cansado.  
Gracias

---

### Post by WHK on 2019-01-18
Hola, eso sucede porque no has hecho el cambio correctamente en el grub, recuerda que cada ves que hagas cambios en el grub una ves que inicies sesión, debes aplicarlos utilizando el comando "**update**-**grub**".

Saludos.

---

