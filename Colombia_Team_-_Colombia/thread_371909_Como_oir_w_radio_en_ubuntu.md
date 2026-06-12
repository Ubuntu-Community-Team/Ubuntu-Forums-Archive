---
title: "Como oir w radio en ubuntu"
date: 2007-02-27
forum: Colombia Team - Colombia
---

### Post by simber on 2007-02-27
Un saludo a todos

Quisiera preguntarles como oir la emisora "la w" en ubuntu. Instale VLC, Realplayer, xmms, y no funciona. 

No se si alguno de ustedes sepa

Muchas gracias

---

### Post by magicfab on 2007-06-08
Qué versión de Ubuntu estás usando ? Cuál es la URL del sitio web de la emisora ?

---

### Post by sirgazil on 2007-06-16
> Qué versión de Ubuntu estás usando ? Cuál es la URL del sitio web de la emisora ?

Yo tengo el mismo problema. Estoy usando Ubuntu 7.04 y el sitio es [[COLOR="DarkRed"]_www.wradio.com.co_[/COLOR]]("http://www.wradio.com.co/"). Uno de los problemas que encuentro es que el enlace para escuchar el audio en vivo abre una página que tiene el reproductor incrustado en ella, o sea que no me permite escoger el reproductor que quiero usar. En mi caso, el reproductor por defecto es Totem, con el que ya he tenido problemas para reproducir audio en flujo, inclusive  audio en ogg. Instalé el plugin de VLC para Firefox y la emisora funcionó; pero unas horas después volví al mismo sitio de la emisora y se volvió a cargar Totem en lugar de VLC.

¿Cómo se puede cambiar el reproductor predeterminado que usa Firefox para reproducir audio?

Saludos,

---

### Post by SEBASTIANFFX on 2007-06-17
Estoy en las mismas :(
Lo mismo pasa con algunas paginas en las que se ofrecen contenido vias streaming como por ejemplo:
[http://www.tvgratis.tv/](http://www.tvgratis.tv/)

---

### Post by sirgazil on 2007-06-17
Bueno, finalmente solucioné mi problema. Hice lo siguiente:

Inicialmente había instalado el plugin de VLC para Firefox (VLC me parece un reproductor muy bueno porque reproduce practicamente todo lo que necesito). Lo hice así:

Abrí un terminal en **Aplicaciones > Accesorios > Terminal**; y escribí:

```
apt-get update
apt-get install mozilla-plugin-vlc
```

Luego abrí Firefox y escribí **about:plugins** (Esto es **about** + **:** + **plugins**, no supe como evitar la carita) en la barra de direcciones para verificar si el plugin se había instalado correctamente. La información me mostraba que sí, decía: **VLC Multimedia Plugin**.

Como después de instalar el plugin el navegador seguía usando Totem como reproductor predeterminado y no pude encontrar en las opciones de Firefox una forma de cambiar esto, decidí desinstalar el plugin de Totem (que me ha servido poco), así:

Abrí el gestor de paquetes Synaptic que está en **Sistema > Administración > Gestor de paquetes Synaptic** y busqué con el criterio **Totem**. En la lista de paquetes apareció la opción **Totem-mozilla**, le di clic derecho, seleccioné **Marcar para eliminar** y apliqué los cambios.

Ahora puedo escuchar la emisora.

[COLOR="Blue"]SEBASTIANFFX[/COLOR], también probé con el sitio [_[COLOR="DarkRed"]http://www.tvgratis.tv[/COLOR]_]("http://www.tvgratis.tv") y funciona.

Espero que les funcione a ustedes también ;)

---

### Post by SEBASTIANFFX on 2007-09-09
Muchas gracias!!! 
ya puedo y escuchar todo el contenido por streaming que quiera! :popcorn::popcorn: :)
Ojala Esto le sirve tambien a otros usuarios ;)

---

### Post by seaq on 2007-10-13
otra forma de escucharla es metiendola en amarik,

crean un nuevo flujo de radio y en el url le meten

mmsh://66.175.96.10/cowradio


y listo!!!

(asi funcionan todas las de caracol)

---

### Post by sirgazil on 2007-10-14
Sí, de esta forma también funciona **seaq**:) De hecho, este fue el primer método que intenté usar para poder escuchar la emisora pero no pude encontrar la dirección al flujo de audio ¿Cómo conseguiste esa dirección **seaq**? Yo busqué en el código de la página y no lo vi.

Por cierto, esta opción no es funcional solo en Amarok sino en cualquier reproductor que pueda abrir direcciones y que acepte el formato del flujo correspondiente.

---

### Post by seaq on 2007-10-26
normalmente intento abrir el enlace por el firefox y luego con wget lo descargo, tradicionalmente los ASX son un archivo apuntando a la direccion, que es lo que sirve. 

lo del mms lo encontre en un bug que reporte por launchpad.

tengo en mi lista por hacer sacar un listado con todas las emisoras pero el trabajo no da espacio .... hehe

---

### Post by por100pre1 on 2007-10-26
Puedes usar streamtuner para guardar esas direcciones facilmente:

```
sudo apt-get install streamtuner
```

---

### Post by angel_buntu2007 on 2007-11-01
:lolflag: Que nota como solucionaron ese problema, no se si lo mismo se puede hacer con la estacion de los Cuarenta Principales COlombia?  la dirección es: [http://www.los40.com.co/](http://www.los40.com.co/) y tiene la opcio de ·Emisora en Vivo". En Windows lo abre directamente con el Windows Media Player, en Ubuntu 7.10 no saca nada. Tambien si alguien tiene el URL de la Emisora se los agradeceria mucho para agregarla al Amarok :)

---

### Post by por100pre1 on 2007-11-04
Bienvenido(a) a los foros. El enlace usa el método mms con auth lo que hace que requiera el enlace que le da la página o el servidor no responde. Ese truco se usa para impedir conneciones directas. La página funciona bien aquí verifique si tiene los codecs instalados. En **Applicaciones> Añadir y quitar...** agregue **Ubuntu restricted extras** y los distintos **Gstreamer plugins**.

---

### Post by classem2003 on 2007-11-08
Esto es lo que yo uso para escuchar caracol cuando estoy trabajando solo con el terminal (no interfaz grafica)

mplayer [http://66.175.96.10/cocarcol?](http://66.175.96.10/cocarcol?)

---

### Post by sirgazil on 2007-11-12
**angel_buntu2007 dijo:**
> ...la dirección es: [http://www.los40.com.co/](http://www.los40.com.co/) y tiene la opcio de ·Emisora en Vivo". En Windows lo abre directamente con el Windows Media Player, en Ubuntu 7.10 no saca nada. Tambien si alguien tiene el URL de la Emisora se los agradeceria mucho para agregarla al Amarok

Hola **angel_buntu2007**:

Probé el sitio de la emisora de los 40 en mi Ubuntu 7.10 y la única opción que veo que dice "Señal en vivo" no funciona como enlace. Sin embargo, encontré esta lista de emisoras en vivo de Caracol radio que incluye la de los 40:

[[COLOR="Sienna"]http://www.caracol.com.co/envivo/[/COLOR]]("http://www.caracol.com.co/envivo/")

A mi me funcionan todas las emisoras listadas ahí usando el plugin de VLC para mozilla.

Sobre el URL de la emisora, no entiendo todavía cómo averiguarlo. Pero **angel_buntu2007**, si usted tiene acceso a un computador con Windows le recomiendo que haga lo siguiente:

**1.** Ingrese a [[COLOR="Sienna"]http://www.caracol.com.co/envivo/[/COLOR]]("http://www.caracol.com.co/envivo/") y seleccione la emisora de los 40.
**2.** Cuando se esté reproduciendo, haga clic derecho sobre el reproductor incrustado en la página y busque una opción que le dé información sobre lo que se está reproduciendo. Estoy casi seguro de que Windows Media Player permite ver la dirección del flujo de audio.
**3.** Ya con la dirección a la mano, puede usarla en la mayoría de los reproductores de Ubuntu.

¡Suerte!

---

### Post by gunnersslash on 2007-12-26
pues gracias a ustedes muchacho, sip, viendo el codigo fuente encontre la mayoria de las direcciones y gracias al post arribita de cassem2003

aqui los encontre, no todas como queria pero si la mayoria

aca dejo el listado, ya las tengo como iuna lista de reproduccion en mi wmp11

caracol radio           [http://66.175.96.10/cocarcol](http://66.175.96.10/cocarcol)
tropicana                [http://66.175.96.10/cotropi](http://66.175.96.10/cotropi)
w radio                   [http://66.175.96.10/cowradio](http://66.175.96.10/cowradio)
los 40 principales   [http://66.175.96.10/co40p](http://66.175.96.10/co40p)
vallenata                [http://66.175.96.10/covalle](http://66.175.96.10/covalle)


bueno y me falto radioactiva y oxigeno que no se podia asi como las anteriores, pero por suerte aparece el codigo donde se hospedan casi todas las emisoras de latinoamerica y salieron aun mas directo, y por si las cambian, ahi me imagino que saldran las anteriores ya mencionadas 



oxigeno              [http://audio2.grupolatinoderadio.com/envivo.ASX?EMI=COOXIGENO](http://audio2.grupolatinoderadio.com/envivo.ASX?EMI=COOXIGENO)
radioactiva         [http://audio.grupolatinoderadio.com/envivo.ASX?EMI=COACTIVA](http://audio.grupolatinoderadio.com/envivo.ASX?EMI=COACTIVA)



todo es gracias a ustedes por eso lo posteo, jejeje nisiquiera estaba inscrito en esta pag

---

### Post by omisaza on 2008-03-19
Hola, solo quiero contar como escucho [www.caracol.com.co/](www.caracol.com.co/)  generalmente funciona para otras de las emisoras relacionadas a caracol, ex: la W  ,la creación y mantenimiento debe estar en las manos de los mismos igualmente usan  .asp  (windows server etc..) ,
hace algunas semanas era fácil, normal, pero algo cambiaron,  y se enredo un poquito , en windows solo hay que esperar unos segundos, pero en linux después de hacer click en el link para escuchar viene una larga espera y luego un error "could not open location" ,

uso Ubuntu gusty , pero versiones anteriores de Ubuntu y en otros distros funciona igual

nota: asumimos que los codec ya están instalados, forma [manual]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html") o automática (ubuntu 7.10)

lo mas facil y como ya lo han dicho aqui es abrir en totem ( o su player favorito) la dirección: mms://66.175.96.10/cocarco y después guarda el link como un playlist ..

pero cuando se llega por el navegador (firefox) :

- Prefiero escuchar las emisoras directamente en totem Movie player por eso siempre tengo instalada una extensión para firefox que me hace posible abrir los archivos directamente en el programa y no con el plugin dentro de la pagina de firefox, muy practico y util para muchas otras cosas . [https://addons.mozilla.org/ja/firefox/addon/446](https://addons.mozilla.org/ja/firefox/addon/446)


- Aparentemente antes del archivo/ link que transmite la emisora se carga un archivo silencio.mp3, por ahi empieza el problema,  se puede ver en el playlist.

- entonces si el playlist solo contiene el link directo mms://66.175.96.10/cocarco  el problema esta resuelto , así que después de esperar el errorcito , elimine las otras entradas en el playlist y deje solo Caracol S.A, -CARACOL RADIO  se guarda y ese es el playlist para usar siempre!!

---

### Post by ABAGAG on 2008-06-17
hola a todos...

hace poco entre al mundo del sofware libre, y ando algo perdido!!... esta página me ha ayudado mucho..

este tema en especial me quito un dolor de cabeza....Gracia

ahora. Yo tengo el plugin de vlc para mozilla.. y no puedo escuchar la emisora desde la página con el enlace "audio en vivo". Gracia al URL que me dieron acá ahora la escucho por el Rhytmhbox.. sin embargo aun no se cómo hacerlo desde el enlace de la página.. me sale un aviso de los 60 años de caracol, y luego donde debería estar el reproductor aparece un área en negro con un aviso entre parentesis que dice: (no video)..ya he quitado por psynaptic el totem , sus plugins, y deje el vcl como reproductor.. nose qué pasa!!
Oviamente esto lo pregunto no para escuchar sino para otras págians similares incluyendo la que aparece un uno de los post...tvgratis.tv.. me sale el mismo aviso..(en el enlace a la emisora  se alcansa a escuchar algo pero está entrecortado)

Pd: tengo hardy , actualizodo, el navegador es firefox 3 :D

---

### Post by ivancamilov on 2008-08-31
Perfecto! ya puedo escuchar Radioactiva en mi Rhythmbox. la url de radioactiva es 
mms://66.175.96.9/coractiva

Saludos!

---

### Post by norprofile1561 on 2009-03-06
Cambiaron algunas url's. Últimamente estoy usando estas:

#!/bin/bash
comando=$1

if [ -z "$1" ] 
then
	echo "Uso: emisoras -<numero emisora>"
	echo "<numero emisora> puede ser:"
	echo "caracol     ___ 1 "
	echo "tropicana   ___ 2 "
	echo "la w        ___ 3 "
	echo "los 40      ___ 4 "
	echo "vallenata   ___ 5 "
	echo "radioactiva ___ 6 "

fi

if [ "$comando" = "-1" ];then
 mplayer mms://66.175.96.9/cocarcol
elif [ "$comando" = "-2" ];then
 mplayer mms://66.175.96.9/cotropi 
elif [ "$comando" = "-3" ];then
 mplayer mms://66.175.96.9/cowradio
elif [ "$comando" = "-4" ];then
 mplayer mms://66.175.96.9/co40p
elif [ "$comando" = "-5" ];then
 mplayer mms://66.175.96.9/covalle
elif [ "$comando" = "-6" ];then
  mplayer mms://66.175.96.9/coractiva
fi

---

### Post by descargado on 2009-03-12
hola a todos, 
Recientemente instale ubuntu y me estoy migrando lentamente a todas las tareas q hacia con windows a linux.

he seguido las instrucciones para instalar el plugin de VLC desinstalando el totem incluso.
efectivamente ahora puedo oir caracol pero el sonido sale con cortes seguidos lo cual no me ocurria cuando escuchaba por windows..
Estare haciendo algo mal  o debo configurar algo en la red?

---

