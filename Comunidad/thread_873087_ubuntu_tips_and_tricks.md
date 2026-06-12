---
title: "ubuntu tips and tricks"
date: 2008-07-28
forum: Comunidad
---

### Post by felipelerena on 2008-07-28
Buenas señores, señoritas,
Estoy dando en 20 dias aprox. una charla de "ubuntu tips and tricks" en las jornadas regionales y estoy recolectando tricks de los miembros de ubuntu-ar para incluir en la charla.

Hace un par de semanas que estoy recolectando por mi cuenta, pero un poco de ayuda y de "inteligencia colectiv ano me vendria mal". Estaria bueno que todos los que tengan algun truco o copado lo manden asi lo incluimos en la charla.
obviamente prometo citar a los colaboradores en la charla.

Saludos,
Lipe

---

### Post by rober-mpp on 2008-07-28
Sin duda, uno que deberia estar:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)


Saludos Felipe

Rober

---

### Post by felipelerena on 2008-07-28
eh???? eso no es un tip... y... vos queres que me asesinen?

---

### Post by crosssover on 2008-07-29
que te parece este [http://dmolinap.blogspot.com/2008/07/metacity-con-composite.html](http://dmolinap.blogspot.com/2008/07/metacity-con-composite.html)

---

### Post by pol666 on 2008-07-30
jajajaj tip no twek. Mira podes hablar de personalizar un desktop. lo bien que puede quedar ubuntu, y podes mostrar algunos trabajos originales como los de Santiago o Valucha o poco originales como algun captura mia Jajajaj.

Eso obvio si vas a estar con alguna pantalla.  Sino  podes hablar un poco de la interaccion entre windows y ubuntu, las particiones ext3 y el soporte a ntfs, o del famoso friver IFS para win que te permite ver las particiones ext en win... Eso mas que nada para sacarle dudas a los usuarios que todavia no lo probaron.

---

### Post by granjero on 2008-07-31
me encantaria participar de la charla? donde la vas a dar? es en bs as?

taria saber de antemano la fecha para pedir el dia en el laburo... jejejeje

salud!

---

### Post by leo_rockway on 2008-08-01
> **granjero said:**
> me encantaria participar de la charla? donde la vas a dar? es en bs as?

taria saber de antemano la fecha para pedir el dia en el laburo... jejejeje

salud!

[http://jornadas.cafelug.org.ar/8/es/home.php](http://jornadas.cafelug.org.ar/8/es/home.php)

---

### Post by User21 on 2008-08-01
TIP: Cuando se instala una webcam (si todo sale bien y la reconoce de una), lo general es que se instalen Cheese, para sacarse fotos facilmente. Pero no siempre Cheese toma el origen de video correcto. Para asegurarse que asi lo haga, ejucuten gconf-editor. Alli se debe modificar la clave Apps/Cheese/Webcam indicandole el dispositivo que responde a la webcam, ya sea /dev/video1, /dev/video1... /dev/videoN 
Whisky!

TIP: Para extraer dispositivos tales como MP3, MP4, discos extraibles, etc, DE MANERA SEGURA, una forma grafica y sencilla es añadiendo a alguno de los paneles, el applet "Montador de discos". Alli apareceran los dispositivos montados, y con un CLIC pueden ser extraidos como corresponde. Muchos usuarios se sienten comodos colocandolo en el extremo derecho del panel inferior, como acostumbraban en otros sistemas.

TIP: Si en tu ordenador hay UNA SOLA CUENTA de usuario y no temes por la seguridad de tus datos, quizas desees quitarle el LOGIN, activando la opcion "Entrada Automatica" en Sistema > Administracion > Ventana de Entrada> Seguridad.

TIP: Si deseas tener en el escritorio los iconos de tu Home, Documentos, Red y Papelera, puedes activarlos activando las propiedades en la clava Apps/Nautilus/Desktop , a traves de gconf-editor.

TIP: Para aligerar un poco la interfase grafica en Gnome, puedes activar la opcion "Reduced Resources" en la clave Apps/Nautilus/Desktop , a traves de gconf-editor.

TIP: Si posees un teclado standard sin teclas multimedia o de acceso rapido, puedes setear algunas funcionalidades basicas mediante Preferencias > Atajos de Teclado. Por ejemplo, yo uso Ctrl + Alt + Flecha Arriba / Abajo  para subir y bajar el volumen general. Las posibilidades son infinitas. 

TIP: Si no deseas que cada vez que insertar un mp3 player, o dispositivos similares, se te abra Rhythmbox, debes personalizar las opciones a gusto, en las preferencias de Nautilus. 

TIP: En las preferencias de Nautilus puedes manejar varios aspectos en como se muestra la informacion de las carpetas y archivos. Desde el tamaño del icono hasta la previsualizacion de los distintos tipos de medios. Tambien puedes organizar la vista del panel izquiero como Arbol, Lugares, etc. 

Ya me acordaré de otros, en casa.

---

### Post by User21 on 2008-08-01
Este trick me lo inventé yo solito! :D

Antes que nada, necesitamos instalar photo-uploader desde Synaptic o via consola:
```
sudo apt-get install photo-uploader
```

Ahora, create un lanzador en el escritorio o en algún panel, con las siguientes características:

Nombre: Photo Upload (o el que desees)
Comando: ```
photo-upload -s imageshack.us $file -B firefox
```
Icono: el que te plazca.

Listo! Al arrastrar cualquier imagen hacia ese ícono, la misma sera subida automáticamente a ImageShack y abrirá en Firefox, mostrando las URLS. 
Puede haber cierta demora: es el tiempo de subida, segun el tamaño de la imagen y la velocidad de red, aunque parezca no estar haciendo nada. 

":) Bueno, eso fue el Photo-Uploader Custom Icon para Ubuntu Hardy Heron, y espero les haya gustado... " Onda Nivel X   xD

---

### Post by pol666 on 2008-08-01
jajaja que buen prog nivel X.


Buena Juan, no sabia la del upload image. No sabes algun programa que suba varias imagenes de una?

Saludos!

---

### Post by faktorqm on 2008-08-04
> **User21 said:**
> 
TIP: Para aligerar un poco la interfase grafica en Gnome, puedes activar la opcion "Reduced Resources" en la clave Apps/Nautilus/Desktop , a traves de gconf-editor.


Hola, che yo no la tengo esa clave, tengo ubuntu 8.04. Esa clave la encontre en apps -> metacity -> general. La active a ver si se me aligera algo.... si no te aviso :lolflag: salu2!!

---

