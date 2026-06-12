---
title: "3 errores que tengo en ubuntu"
date: 2010-03-30
forum: Centroamerica Team
---

### Post by kevin3377 on 2010-03-30
Hola porfavor ayudenme a arreglar estos errores :-P Soy De Heredia Hehe...

Bno mi primer error es que al estar toqueteando la barra de arriba elimine el boton que dice el nombre de usuario y a la par viene el signo de como de "power" y ya no me sale le doy click derecho>añadir al panel>Miniaplicacion Cliente de terminal server (eso es para ver ese boton) y me sale el siguiente mensaje:

[IMG]http://i292.photobucket.com/albums/mm11/kevin_lobo/Pantallazo.png[/IMG]

Mi segundo error es de la resolucion de pantalla... Mi pantalla se ve super bien en la resolucion 1024x700 pero en Sistema>Preferencias>Pantalla no me sale esa opcion!!! Solo aveces y le doy en aplicar y al reiniciar me aparece otra vez en 800x600 y ya no me sale la opcion de 1024x700... Alguna solución?

Mi tercer error es con compiz fusion... Cuando lo activo en Select window manager>Compiz

Me quita los bordes de las ventanas y no puedo hacer nda... 

Esto es lo que me sale al usar el comando lspci:

00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

Ayudenme porfavor

---

### Post by kevin3377 on 2010-03-30
Perdon se me olvidaba es Ubuntu 9.10

---

### Post by gabo.cr on 2010-04-02
Hola

El applet de "Terminal Server" no es para agregar el botón para cambiar de usuario o apagar el sistema.
Pero si quieres agregarlo al Panel, hay un "bug" reportado sobre ese error.
[https://bugs.launchpad.net/tsclient/+bug/420208](https://bugs.launchpad.net/tsclient/+bug/420208)

El asunto con la resolución y con Compiz son parte del mismo problema con ProSavage8 KM266.
Tienes que activar la aceleración 3D en esa tarjeta. Pero la tarjeta que tienes no es compatible.
Antes había una manera de solucionar esto con Xorg, pero Karmic ya no utiliza ese archivo.
Sin embargo, la resolución debería funcionar sin Compiz, no?

---

