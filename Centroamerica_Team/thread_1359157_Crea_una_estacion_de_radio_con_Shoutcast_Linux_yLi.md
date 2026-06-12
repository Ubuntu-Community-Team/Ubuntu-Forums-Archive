---
title: "Crea una estacion de radio con Shoutcast Linux yListen2MyRadio!!!"
date: 2009-12-19
forum: Centroamerica Team
---

### Post by JosueAquino on 2009-12-19
Bueno, estuve buscando en internet como hacer una radio y creo que lo encontré.

1ºPaso:Nos descargamos el shoutcast(para conectarnos a listen2myradio) de [http://yp.shoutcast.com/downloads/sc_trans_posix_040.tgz]("http://yp.shoutcast.com/downloads/sc_trans_posix_040.tgz")

2ºPaso:Nos registramos en Listen2Myradio.com:
[IMG]http://img51.imageshack.us/img51/7106/paso1j.png[/IMG]
[IMG]http://img51.imageshack.us/img51/8995/paso12.png[/IMG]
[IMG]http://http://img51.imageshack.us/img51/7003/paso2f.png[/IMG]
[IMG]http://img51.imageshack.us/img51/272/paso22.png[/IMG]

3ºPaso: Nos Logeamos:
[IMG]http://img51.imageshack.us/img51/1156/paso3.png[/IMG]

Al conectarnos veremos unas letras en rojo porque no hemos instalado y encendido nuestra radio, ahora lo haremos, le damos a Radio Installation:
[IMG]http://img121.imageshack.us/img121/4840/paso4f.png[/IMG]

Seleccionasmo nuestro server:
[IMG]http://img121.imageshack.us/img121/9536/paso42.png[/IMG]

5º Paso: Descomprimios el shoutcast:
[IMG]http://img693.imageshack.us/img693/4273/paso5.png[/IMG]

Segunda Parte despues!!!

---

### Post by JosueAquino on 2009-12-19
6º Paso: Segun como este en el servidor editamos el el archivo sc_trans.conf:
[IMG]http://img97.imageshack.us/img97/3918/paso52.png[/IMG]

7º Paso: Nos vamos a la carpeta donde tengamos la musica EN FORMATo MP3 con terminal y escribimos:
```
find /ruta/de/tu/carpeta -type f -name "*.mp3" > example.lst 
```
La lista quedaria asi:
[IMG]http://img12.imageshack.us/img12/1861/paso6.png[/IMG]

8º Paso: en terminal abrimos el archivo sc_trans_linux que esta en la carpeta descomprimida:
[IMG]http://img691.imageshack.us/img691/4972/paso72.png[/IMG]
[IMG]http://img97.imageshack.us/img97/2890/paso73.png[/IMG]

Si tenemos encendido el server en listen 2 my radio(los datos del server deven estar en verdie si esta on) podremos conectarnos a la radio, de lo contrario, no.

Y listo, tu radio esta lista para musiquear xD!

Con esto me desipido de este post comunidad Ubuntera Sv!!!

Aquino.

---

