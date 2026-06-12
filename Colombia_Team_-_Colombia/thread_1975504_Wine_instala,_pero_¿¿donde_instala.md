---
title: "Wine instala, pero ¿¿donde instala ???"
date: 2012-05-07
forum: Colombia Team - Colombia
---

### Post by memo85 on 2012-05-07
Hola a todos, le cuento mi problema esperando alguien me pueda ayudar a solucionarlo:
Tengu ubuntu 10.04, todo al parecer me fucniona de maravilla, me ha gustado mucho este sistema operativo, ya que vengo de windows, pero para nadie es un secreto que el openoffice es un asco, y definitivamente el office de windows es insuperable hasta el momento.
Asi que he instalado Wine para emular &#341;esisanmente este programa, pues lo necesito con mucha frecuencia.
He instalado wine de la siguiente manera:
root@jj-laptop:# apt-get install wine1.2
[SIZE="1"]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  libmpg123-0 ttf-droid ttf-symbol-replacement ttf-umefont winbind wine1.2-gecko winetricks
Paquetes recomendados
  wine1.4 wine cxoffice5 cxgames5[/SIZE]
....
..
..
.


Y el proceso termina bn.
Luego escribo en la consola, siendo root,:apt-get update
Todo bn, luego instalo las librerias que descarga winetricks:
./winetricks gdiplus riched20 riched30 msxml3 msxml4 msxml6 corefonts tahoma vb6run vcrun6 msi2

Y bien, empiezo a instalar un poco de cosas al estilo de windows....bueno , en fin, termino de instalar todo, en el menu de aplicaciones, ya me sale Wine, y listo.

Ahora procedo a instalar office 2007; abro la carpeta en donde tengo el instalador, le doy permisos de ejecucion, (con click derecho o por consola con chmod....), y comienza la instalacion, pero inmediatamente me arroja un error, y no permite seguir instalando, diciendo que windows ha encontrado un error y que no puede continuar la instalacion.

Asi que se me occurrió, desde la consola, loguearme como root, y ejecutar desde ella el comando : wine INSTALL.EXE (estando dentro de la carpeta donde tengo el .exe de office, y siendo root), y milagrosamente, el programa se instala si ningun problema. Parece que habia que hacerlo siendo root. Pero el pequeño problema es que office no aparece en Aplicaciones> Wine , no aparece absolutamente nada, y he buscado en las carpetas que crea Wine , z, y, h, en fin, en todo el sistema, y no encuentro donde esta office, hice la prueba instalando winamp, y los mismo, solo se me instalaba si desde la terminal lanzaba el .exe pero siendo root, y al terminar la instalacion, trataba de buscar en Apliacaciones> Sonido y Video , y nada, no aparecia por ningun lado.

Por tanto procedí a eliminar wine, desde Centro de software de ubuntu y listo, luego ecribi en una terminal:
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
para borrar todol lo que tubiera que ver co wine de mi sistema.

Procesdí a isntalar wine nuevamente, pero esta vez sin ser root, solo escribía :
sudo apt-get install wine1.2
pass: 
y listo, comensaba de nuevo pero repito, esta vez sin ser root.
Al momento de instalar de nuevo SETUP.EXE no me deja instalarlo si no soy root desde la consola. 

Pero vuelve y juega, no me aparecia instalado office por ningun lado, y ya estoy cansado de hacer lo mismo, y no se que mas hacer.


Alguien que me ayude, y me diga cual es el problema.


Gracias

---

### Post by rodsarm on 2012-05-08
> **memo85 said:**
> Hola a todos, le cuento mi problema esperando alguien me pueda ayudar a solucionarlo:
Tengu ubuntu 10.04, todo al parecer me fucniona de maravilla, me ha gustado mucho este sistema operativo, ya que vengo de windows, pero para nadie es un secreto que el openoffice es un asco, y definitivamente el office de windows es insuperable hasta el momento.
Asi que he instalado Wine para emular &#341;esisanmente este programa, pues lo necesito con mucha frecuencia.
He instalado wine de la siguiente manera:
root@jj-laptop:# apt-get install wine1.2
[SIZE="1"]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  libmpg123-0 ttf-droid ttf-symbol-replacement ttf-umefont winbind wine1.2-gecko winetricks
Paquetes recomendados
  wine1.4 wine cxoffice5 cxgames5[/SIZE]
....
..
..
.


Y el proceso termina bn.
Luego escribo en la consola, siendo root,:apt-get update
Todo bn, luego instalo las librerias que descarga winetricks:
./winetricks gdiplus riched20 riched30 msxml3 msxml4 msxml6 corefonts tahoma vb6run vcrun6 msi2

Y bien, empiezo a instalar un poco de cosas al estilo de windows....bueno , en fin, termino de instalar todo, en el menu de aplicaciones, ya me sale Wine, y listo.

Ahora procedo a instalar office 2007; abro la carpeta en donde tengo el instalador, le doy permisos de ejecucion, (con click derecho o por consola con chmod....), y comienza la instalacion, pero inmediatamente me arroja un error, y no permite seguir instalando, diciendo que windows ha encontrado un error y que no puede continuar la instalacion.

Asi que se me occurrió, desde la consola, loguearme como root, y ejecutar desde ella el comando : wine INSTALL.EXE (estando dentro de la carpeta donde tengo el .exe de office, y siendo root), y milagrosamente, el programa se instala si ningun problema. Parece que habia que hacerlo siendo root. Pero el pequeño problema es que office no aparece en Aplicaciones> Wine , no aparece absolutamente nada, y he buscado en las carpetas que crea Wine , z, y, h, en fin, en todo el sistema, y no encuentro donde esta office, hice la prueba instalando winamp, y los mismo, solo se me instalaba si desde la terminal lanzaba el .exe pero siendo root, y al terminar la instalacion, trataba de buscar en Apliacaciones> Sonido y Video , y nada, no aparecia por ningun lado.

Por tanto procedí a eliminar wine, desde Centro de software de ubuntu y listo, luego ecribi en una terminal:
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
para borrar todol lo que tubiera que ver co wine de mi sistema.

Procesdí a isntalar wine nuevamente, pero esta vez sin ser root, solo escribía :
sudo apt-get install wine1.2
pass: 
y listo, comensaba de nuevo pero repito, esta vez sin ser root.
Al momento de instalar de nuevo SETUP.EXE no me deja instalarlo si no soy root desde la consola. 

Pero vuelve y juega, no me aparecia instalado office por ningun lado, y ya estoy cansado de hacer lo mismo, y no se que mas hacer.


Alguien que me ayude, y me diga cual es el problema.


Gracias


Bueno difícilmente Wine le ayudara con el Office, salvo que se consiga una versión portable.  Pruebe instalando LibreOffice que nada tiene que envidiarle al Office de Microsoft.

La consigue en esta dirección [http://www.libreoffice.org/download/](http://www.libreoffice.org/download/), le va gustar. Y es libre.

---

### Post by rodsarm on 2012-05-08
> **rodsarm said:**
> Bueno difícilmente Wine le ayudara con el Office, salvo que se consiga una versión portable.  Pruebe instalando LibreOffice que nada tiene que envidiarle al Office de Microsoft.

La consigue en esta dirección [http://www.libreoffice.org/download/](http://www.libreoffice.org/download/), le va gustar. Y es libre.

Pero si se quiere embarcar definitivamente en ese proceso, que la experiencia dice que tendrá fallas en el transcurso de los días ejecutando Officce, haga esto:

sudo apt-get install wine            (Instala wine)
sudo apt-get install cabextract      (instala cabextract)

----ahora use un scrip que le sube librerias necesarias---
----lo halla en: kegel.com--- o escribe esto...

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
chmod +x ./winetricks

[I]Esto instalará todas las librerías y DLLs necearias que requiere Office 2007. (consecuentemente, también anteriores) ./winetricks gdiplus riched20 riched30 msxml3 msxml4 msxml6 corefonts tahoma vb6run vcrun6 msi2. Se paciente mientras la instalación se completa, este escript trabaja duro ahorrandote horas de trabajo.
[/I]

Ahora si, ubica el CD en la unidad y ejecuta

wine pathToCD/setup.exe

y ya!! listo..eso comenzara el proceso de instalación..... pero insisto, le dará guerra de vez en vez..mejor revise y quédese con LibreOffice.... le encantara!!!!

---

### Post by memo85 on 2012-05-09
> **rodsarm said:**
> Pero si se quiere embarcar definitivamente en ese proceso, que la experiencia dice que tendrá fallas en el transcurso de los días ejecutando Officce, haga esto:

sudo apt-get install wine            (Instala wine)
sudo apt-get install cabextract      (instala cabextract)

----ahora use un scrip que le sube librerias necesarias---
----lo halla en: kegel.com--- o escribe esto...

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
chmod +x ./winetricks

[I]Esto instalará todas las librerías y DLLs necearias que requiere Office 2007. (consecuentemente, también anteriores) ./winetricks gdiplus riched20 riched30 msxml3 msxml4 msxml6 corefonts tahoma vb6run vcrun6 msi2. Se paciente mientras la instalación se completa, este escript trabaja duro ahorrandote horas de trabajo.
[/I]

Ahora si, ubica el CD en la unidad y ejecuta

wine pathToCD/setup.exe

y ya!! listo..eso comenzara el proceso de instalación..... pero insisto, le dará guerra de vez en vez..mejor revise y quédese con LibreOffice.... le encantara!!!!



Gracias por responder a mi mensaje. 

Le comento que por fin logré instalar Office 2007 en mi laptop, y luego de formatear de nuevo, porque pensé que habia desconfigurado algo del sistma, encontré el problema.

Resulta que yo instalaba Wine desde la consola, algo asi como:
apt-get install wine1.2
Lo anterior sin ser root.
paso a seguir, descargaba winetriks, y procedia a insalarlo con:
./winetricks gdiplus riched20 riched30 msxml3 msxml4 msxml6 corefonts tahoma vb6run 
y bueno, lo normal, se abria el navegador, descargaba el archivo, lo copiaba en la carpeta que se abria tambien, luego volví a a ejecutar el comando anterior, y bueno, en fin todo normal.

Luego procedia a instalar office, desde el SETUP.EXE que estaba en mi otro disco duro.
y era ahí donde me generaba el error.
Pues decubrí que lo que pasaba era que en la configurarion de wine, cuando recien se instalaban las librerias, y sin instalar aun office, en la pestaña "aplicaciones", obviamente solo decia "Configuracion &#7765;or defecto", es decir, solo aparecia como la imagen 1, pero sin word, exel ni powerpoint,  cuando hacia click ahí, y luego iba a "librerias", me aparecian ya señaladas un poco de librerias que Winetrics habia descargado. Pues bien, lo que hice fue eliminar cada una de esas librerias, -> aplicar-> aceptar. y que quedara tal cual la imagen 2.

Ahora procedí de nuevo a instalar Office, dando doble click sobre el *.exe del programa, y comenzó la instalación perfectamente ahora si.
al termina la instalacion, fuí a Aplicaciones->Wine->Programas, y ya aparecia Microsoft Office, (cosa que antes, a pesar de que instalaba , no aparecia ni en el menu, ni en c: )

Luego traté de abrir word, y me botó un error que deca algo como que word se tubo que cerrar inesperadamente . bla bla bla....
Lo que hice ahora fue : Aplicaciones->Wine->Configurar wine
y dejar todo como en las imagenes que muestro a continuacion, y listo, word, exel y ppt fucnionando al 100%.

Exel, word, y ppt, deben dejarle a cada uno las librerias de la imagen, no solamente a uno de ellos, porque si nó , solo va a servir al que le agreguen las librerias.  En las imagenes solo muentro las librerias de exel (figura 4), pero son las mismas de word y ppt.


Ojalá le sirva a alguien mi experiencia.

Salu2

---

