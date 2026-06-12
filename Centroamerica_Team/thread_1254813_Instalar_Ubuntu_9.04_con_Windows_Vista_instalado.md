---
title: "Instalar Ubuntu 9.04 con Windows Vista instalado"
date: 2009-08-31
forum: Centroamerica Team
---

### Post by dan_06 on 2009-08-31
hola Como stan todos.

Quisiera q me aclararan algunas dudas de instalar ubuntu en mi laptop que tiene Windows Vista Bussines,

**Ok es que quiero instalar ubuntu 9.04 y he leido que instalarlo con  windows vista ya instalado da problemas quiero saber si es verdad**.

---

### Post by hockeytux on 2009-08-31
Ubuntu hace la particion automaticamente... es mas mas problematico instalar windows con ubuntu instalado. Con windows primero, y dual-boot no hay problemas.

---

### Post by dan_06 on 2009-08-31
Ok entonces no hay problemas entonces ??? y dual-boot como que es, lo entiendo como q es el Grub,

Y otra consulta si no es mucha molestia :D ya q me dices q no hay problemas voy a hacer una particion en el dico de unos 15 GB y al arrancar la laptop, es necesario modificar que SO arranca primero o el mismo Grub hace eso.

Y gracias por tu pronta respuesta

---

### Post by adrianlancer on 2009-09-01
el grub automaticamente pone el ubuntu a bootear primero pero es algo ke puedes editar si lo nesecitas

---

### Post by jjgomera on 2009-09-01
asegurarte que no vas a tener problemas no, lo que tienes que hacer es usar el liveCD antes de instalarlo y comprobar que todo funciona bien, que detecta los discos duros, el audio, la tarjeta gráfica, la red

con windows vista no es el problema, pero si hay algunos portatiles que hay que cambiar opciones en la bios, la compatibilidad sata del disco duro, para hacerlo funcionar con cualquier linux o xp mientras que con vista va bien por defecto

---

### Post by Nugar on 2009-09-01
Con respecto al GRUB, es simplemente un menu que te sale en la pantalla para que escojas el SO que quieres arrancar.

Esta seteado para que arranque Ubuntu automaticamente, pero se puede editar ara que arranque Vista por defecto.

En cualquier caso, el te da como 30 segundos para elegir.

---

### Post by gmunioz on 2009-09-02
Hola da...:

Sugerencias:

1º) Prueba con el live-cd si te reconoce Ubuntu todos

los componentes del ordenador.

2º) Desde Windows, con su administrador de dispositivos

reduce la partición y deja entre 10 y 15 gigas libres,

sin particionar.

3º) Desde el live-cd, inicia la instalación y cuando llegues

a particionamiento, elige instalar en el espacio contiguo libre

Ubuntu hará todo por tí.

Si solo quieres probar Ubuntu, inserta en cd en una sesión 

Windows e instalaló con wubi como una aplicación, no tendrás

todas las ventajas de Ubuntu y seguiras con las inseguridades

de Windows, pero podrás probar sin particionar, dejando esto

para cuando estes más familiarizado con discos y particiones.

---

### Post by dan_06 on 2009-09-04
Hola a todos ;

Gracias GRacias por todas sus repuestas que son muy buenas.

Pero me he metido en un dolor de cabeza, por favor  Ayudenme que he buscado en toda la Web y he encontrado algo que me ayude 

 Me paso que probando el LivecD de ubuntu 9.04 experimentando toque la opcion de particiones que viene en el liveCD y se me borro todo el dico duro, pense algo que no debia hacer instalar el ubuntu despues el vista,

al reiniciar me percatee que el vista no salia en el GRUB 

depues busque para desintalar el ubuntu perfecto se desintalo, pense que se hiba a ir con todo y GRUB pero no fue asi 

el fuc... GRUB se quedo ahi mandandome un error 22 como he leido no encuentra un SO pro tiene instalado el vista.

Ya he probado en insertanado cd de XP para ver si me formateaa y nadaaa me manda un error como queno renoce ningun disco.

Por favor diganme como puede desabilitar ese GRUB para q mi SO me arranque de manera normall 

o si se puede desabilitar con el Live cd de ubuntu.

Porfavor ayudenme con este dolor de cabeza [-o<

disculpen por escribir tanto:(

---

### Post by Nugar on 2009-09-04
Dime algo... cuando booteas tu laptop, te sale un mensaje que dice: presione F11 para restaurar (o algo similar?)

Si es asi, al presionar eso, se restaurara Vista, pero eso si, quedará como una instalacion de fabrica, sin nada de tus datos.

Si esto no es asi, la otra opcion es buscar un disco de Vista y formatear la maquina desde ahi.

Si necesitas recuperar tus archivos, bootea desde el livecd, entras a tus archivos, los guardas en un USB y luego haces tu reformateo.

Espero que estas ideas te ayuden a encontrar un curso de accion.

De todos modos, aqui te pongo una busqueda de Google (Google es tu amigo) donde puedes encontrar informacion acerca de como quitar GRUB y dejar Vista booteando norma. Eso si, esta en ingles.

[http://www.google.com/search?hl=en&source=hp&q=uninstalling+grub+and+leaving+vista+booting+normally&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&source=hp&q=uninstalling+grub+and+leaving+vista+booting+normally&aq=f&oq=&aqi=)

Suerte,

---

### Post by eivar on 2009-09-04
dan_06 entendí mal o borraste todo el disco duro de tu máquina?
Si no es el caso prueba lo que te dice Nugar,
si es el caso :(, supongo que sacaste respaldos de tus datos antes de intentar instalar ubuntu o tendras que usar una herramienta para recuperar archivos borrados.

Salu2.

---

### Post by dan_06 on 2009-09-08
Gracias nugar por el consejo pude arreglar el dolorcito de cabeza como me dijistes, busque un cd live de xp pro no me sirvio, pero tuve q usar uno q tenia el Windows7 q tuve q formatear todo para despues meter el cd de recuperacion q tenia de windows vista.
:)

---

