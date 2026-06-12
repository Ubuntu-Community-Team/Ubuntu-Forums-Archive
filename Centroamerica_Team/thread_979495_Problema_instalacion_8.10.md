---
title: "Problema instalacion 8.10"
date: 2008-11-12
forum: Centroamerica Team
---

### Post by meldon12 on 2008-11-12
Que tal amigos, en esta ocasion mi problemas es que cuando intento instalar el ubuntu 8.10, en el live cd al empezar a cargar aparece arriba un error que dice "Unable to load System Description Tables" o algo asi, y cuando instalo todo va bn, normal, pero al reinicra para utilizar el SO paarce hasta el incio de sesio y despues no carga la interfaz solo se ve el puntero y queda todo negro, yal o he instalado 3 veces bajando cada vez de nuevo, por DD y por torrent, la ultima vez (hoy ) baje el alternate para ver q tal y nada seguia igual, hasta netre por la temrinal y use dpkg-reconfigure xserver-xorg pero nada, solo me ponia a configurar el teclado peor en ingun momento algo relacionado con el video o la interfaz, al fianl terminaba volviendo al Hardy q no me falla xD.

espero que alguien sepa q puede ser, auanq creo q talves sea q se descarga mal, pero 3 veces?? y tras de eso por torrent q verifica los datos a cada rato.

saludos

meldon12

---

### Post by eivar on 2008-11-12
Hola meldon, para configurar la interfaz gráfica en Hardy se puede hacer con sudo configdisplay-gtk.

Prueba a ver si esto te sirve para configurar tu 8.10.

Saludos.

---

### Post by meldon12 on 2008-11-12
muchas gracias eivar, lo voy a intentar cuando tenga tiempo ya q estoy algo ocupado con un proyecto de la U xD, ojala me funciono y les cuento.

saludos

meldon12

EDITO

lo acabo de probar en el hardy y me dice q ese cokmando no existe XD, 

saludos

---

### Post by eivar on 2008-11-12
Hola meldon ¿No existe? Que extraño yo lo he usado en el 8.04 y el 8.10, cuando lo instalé este último en la pc de un amigo.

Bueno revisa si lo escribiste bien o si de pronto fui yo el que lo escribió mal.

Ahora no estoy en casa pero llego en un momento y verifico.

Saludos.

---

### Post by meldon12 on 2008-11-13
mira aqui te dejo el screenshot, pa q veas q no sire el comando xD

saludos

---

### Post by eivar on 2008-11-13
Ok meldon es cierto no sirve porque lo escribí mal el comando correcto es 
**[COLOR=DarkRed]sudo displayconfig-gtk [/COLOR]**

Saludos.

---

### Post by meldon12 on 2008-11-14
si ya sirve, muchas gracias, ahora una pregunta xD, si no carga la interfaz y solo entro por terminal... como podre usar ese comando si lo q hace es abrir una ventana, que, por cierto, necesita la interfaz??? jaja XD.

saludos y gracias

meldon12

---

### Post by eivar on 2008-11-14
Hola meldon,

por favor mira [aqui]("https://wiki.edubuntu.org/X/DisplayConfigGtk").

Un día por estar instalando un kernel rt de esos que trae ubuntustudio se me tildeo la pc de manera que no arrancaba el entorno gráfico correctamente pasando a una resolución muy mala y automáticamente lanzó esta aplicación para que pudiera reconfigurar el entorno gráfico.

La idea que tengo es:
* reconfigura manualmente el xorg.conf (/etc/X11/xorg.conf) para que use el driver generico **vesa** que soporta todas las tarjetas existentes pero te da una resolución muy mala.
* reinicia el entorno gráfico y una vez en el lanza esta aplicación, luego deberías ser capaz de reconfigurar y el entorno y lo más importante probar distintas combinaciones a ver cual responde mejor, por ejemplo usar el driver nvidia a una resolución de 1024x768 si todo va bien prueba una resolución mayor hasta que encuentres la que mejor funcione.

Suerte y nos cuentas como te va.
Saludos

---

### Post by meldon12 on 2008-11-14
tio no puede ser, me lees la mente, exactamente vine aqui para preguntarte sobre VESA y te me adelantastes, estaba leyendo de un tio q le paso lo mio y descargo el xserver-xorg-video-vesa, despues se escribe startx, y luego configura el xorg.conf, por cierto, nose si conecen esto:

[http://www.googlubuntu.com](http://www.googlubuntu.com)

muy buena esa pagina, ya se imaginaran q es por el nombre.

muchas gracias eivar, lo intentare ya mismo, pero instalando como 2do sistema el 8.10 para no formatear

saludos

meldon12

---

### Post by meldon12 on 2008-11-15
al final instale el xubuntu 8.10, salia el mismo error pero cargaba todo normal y hasta ahora no he tenido ningun problema.

Igual muchas gracias por el interes en mi problema

saludos

---

### Post by meldon12 on 2008-11-16
Tienes algunos cuelgues aveces el xfce, pero bueno, va volando igual, me gusta, mas adelante se q estara mucho mejor. 

Pero en general esta muy bn el xubunu, de verdad q es rapido.

saludos

---

