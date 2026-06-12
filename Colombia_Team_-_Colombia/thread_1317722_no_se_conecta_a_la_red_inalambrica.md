---
title: "no se conecta a la red inalambrica"
date: 2009-11-07
forum: Colombia Team - Colombia
---

### Post by aprend_edd on 2009-11-07
hola como están. Ando de nuevo por acá en el foro para pedir ayuda. 

Bueno el problema es el siguiente: hace mas o menos un mes tuve que parar de usar el ubuntu por cuestiones académicas y ahora que ya tengo posibilidad de usarlo de nuevo surgió lo siguiente:

-Primero se dañó el ubuntu y no se como, pero bueno ya lo arreglé, me tocó instalarlo de nuevo.

-Ahora si el problema principal. Hace poco me instalaron la red inalambrica en la casa y el pc trabaja de maravilla en windows. Lo que pasa es que el ubuntu no me quiere conectar a internet, me pide la contraseña y al ingresarla intenta conectarse pero no deja porque cuando lo intenta el ubuntu me cambia la contraseña.

lo mas extraño es que en la única parte en donde no se conecta a red inalambrica es en mi casa.

entonces lo que quiero saber es como configurar la conexion para que siempre se conecte y no me cambie la contraseña.

Agradezco de antemano la ayuda prestada.

El tipo de seguridad es WPA2. La tarjeta es Ralink 802.11n wireless LAN card. el pc es un ACER 4535, ubuntu 9.04.

---

### Post by CdK1 on 2009-12-22
Trata de configurar con "wicd", es fácil y ligero, también intenta conectar mediante la consola y desde otra terminal haz un dmesg y/o un tail, para ver que es lo que está pasando...

---

### Post by dirakx on 2010-01-08
Tu applet de network manager de gnome debe hacer eso por defecto, el solo te pide la contraseña de sudo para almacenar las contraseñas permanentemente.

---

