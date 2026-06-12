---
title: "Comparte tu escritorio [Lucid]"
date: 2010-05-23
forum: Comunidad
---

### Post by Fisaulerod on 2010-05-23
Aqui va el mio:
[ATTACH]157992[/ATTACH]

---

### Post by nechus on 2010-05-23
Y el mío!

Lo que ven es:
Fondo de pantalla: [http://www.zastavki.com/eng/Creative_Wallpaper/wallpaper-14919-2.htm](http://www.zastavki.com/eng/Creative_Wallpaper/wallpaper-14919-2.htm)
Tema GTK: Muku ( [http://browse.deviantart.com/?q=muku#/dxf844](http://browse.deviantart.com/?q=muku#/dxf844) ) Claro que modifiqué un poco el tema para Emerald porque trae originalmente los botones a la izquierda.
Dock (barra inferior): AWN, estilo Floaty, fondo Dust.
El ícono naranjo de Ubuntu lo corté del logo original ( [http://ubuntulife.files.wordpress.com/2010/03/blackeubuntulogo.png](http://ubuntulife.files.wordpress.com/2010/03/blackeubuntulogo.png) )

---

### Post by 3nG3ndR0 on 2010-05-25
Distro: Ubuntu 10.04
GTK: Elementary EM 0.4 mod Nuala
Iconos: Elementary mod by me
Emerald: Nuala
Dock: AWN, Theme: Plastic
Appet: Gobal Menu

---

### Post by marito1053 on 2010-05-30
Presentandoles mi Escritorio espero les agrade...


[IMG]http://i621.photobucket.com/albums/tt298/1053marito/lts1.jpg[/IMG]

[IMG]http://i621.photobucket.com/albums/tt298/1053marito/lts.jpg[/IMG]


Distro: Ubuntu 10.04 LTS
GTK: Smee
Iconos: meliaeSVG + Pry Aluminiun
Emerald: Dots con botones a la izquierda
Dock: AWN, iconos: Basic5 Textual (mod)
Appet: Gobal Menu, conky, covergloobus theme Corner, sonata + MPD,
wallpaper: Aurora_mods

:guitar:

---

### Post by themasterdark on 2010-05-31
[ATTACH]158855[/ATTACH]

[ATTACH]158856[/ATTACH]

Bueno ese es mi escritorio no tengo muchas ganas de escribir jaja xD

---

### Post by Damixx on 2010-05-31
che que significa quote?

---

### Post by marito1053 on 2010-05-31
Significa Citar....

Y cuando tengas dudas asi... usa algun traductor asi no se genera mucho spam....

cuidate...:P

---

### Post by dierocck on 2010-06-06
[[IMG]http://img153.imageshack.us/img153/4382/pantallazo4j.th.png[/IMG]](http://img153.imageshack.us/i/pantallazo4j.png/)



SO = Lucid Lynx
Emerald = Bump
Iconos = black and white
Wallpaper = road

Tint2, lyrics screenlets, covergloobus

---

### Post by Fisaulerod on 2010-06-17
> **marito1053 said:**
> Presentandoles mi Escritorio espero les agrade...


[IMG]http://i621.photobucket.com/albums/tt298/1053marito/lts1.jpg[/IMG]

[IMG]http://i621.photobucket.com/albums/tt298/1053marito/lts.jpg[/IMG]


Distro: Ubuntu 10.04 LTS
GTK: Smee
Iconos: meliaeSVG + Pry Aluminiun
Emerald: Dots con botones a la izquierda
Dock: AWN, iconos: Basic5 Textual (mod)
Appet: Gobal Menu, conky, covergloobus theme Corner, sonata + MPD,
wallpaper: Aurora_mods

:guitar:

¿Cómo sacaste la flechita que aparece en el ícono del menu principal de gnome?

---

### Post by 3nG3ndR0 on 2010-06-18
> **Fisaulerod said:**
> ¿Cómo sacaste la flechita que aparece en el ícono del menu principal de gnome?

de la siguiente manera.

```
sudo apt-get install apt-build
while configuring, choose your processor type 
sudo apt-build source gnome-panel
sudo apt-get build-dep gnome-panel
cd /var/cache/apt-build/build/
sudo gedit gnome-panel-*/gnome-panel/panel-menu-button.c
```

busca e edita

> button = g_object_new (PANEL_TYPE_MENU_BUTTON,
"menu-path", menu_path,
"custom-icon", custom_icon,
"tooltip", tooltip,
"use-menu-path", use_menu_path,
"use-custom-icon", use_custom_icon,
"has-arrow", **TRUE**,
NULL);


por

> button = g_object_new (PANEL_TYPE_MENU_BUTTON,
"menu-path", menu_path,
"custom-icon", custom_icon,
"tooltip", tooltip,
"use-menu-path", use_menu_path,
"use-custom-icon", use_custom_icon,
"has-arrow", **FALSE**,
NULL);

guarda y cierra

```
cd gnome-panel-*/
sudo ./configure
[i]in case there are still some missing dependencies (build-dep may miss something), install them manually [ most of them are the -dev packages, so use synaptic for that - **for example** when it shows **No package 'libgnomeui-2.0' found**
 , just search in Synaptic Package Manager for libgnomeui (**forget about -2.0 or any other number**) and install the **-dev** package, **libgnomeui-dev**.][/i]
sudo make
sudo make install
sudo killall gnome-panel

```

---

### Post by baila0 on 2010-07-10
Muy wenos todos...

Una duda, qué hay que instalar para que el panel de arriba funcione "al estilo Mac"?

Gracias

---

### Post by marito1053 on 2010-07-10
> **baila0 said:**
> Muy wenos todos...

Una duda, qué hay que instalar para que el panel de arriba funcione "al estilo Mac"?

Gracias

Que hay bro... imagino que te refieres a donde aparece Escritorio, Archivo, Editar, Ver, Lugares y Ayuda esto se llama **Global Menu** te dejo este link [http://ubuntulife.wordpress.com/2010/05/25/instalando-global-menu-applet-en-ubuntu-10-04-lucid-lynx/]("http://ubuntulife.wordpress.com/2010/05/25/instalando-global-menu-applet-en-ubuntu-10-04-lucid-lynx/")
Alli puedes ver la instalacion y despues lo añades al panel y listo...
Cuidate y Bendiciones...


.

---

### Post by baila0 on 2010-07-10
> **marito1053 said:**
> Que hay bro... imagino que te refieres a donde aparece Escritorio, Archivo, Editar, Ver, Lugares y Ayuda esto se llama **Global Menu** te dejo este link [http://ubuntulife.wordpress.com/2010/05/25/instalando-global-menu-applet-en-ubuntu-10-04-lucid-lynx/]("http://ubuntulife.wordpress.com/2010/05/25/instalando-global-menu-applet-en-ubuntu-10-04-lucid-lynx/")
Alli puedes ver la instalacion y despues lo añades al panel y listo...
Cuidate y Bendiciones...


.

Gracias compadre !!
Me funciona perfecto, mucho mas cómodo

---

### Post by Superace on 2010-07-10
Buenas a todos... soy nuevo en el foro y también en ubuntu. Tengo nociones muy básicas de linux, pero de todas formas intentare ser de ayuda en este foro... y obviamente recibir ayuda de este gran mundo del software libre.

Este es mi escritorio actual:

[IMG]http://i839.photobucket.com/albums/zz315/superace2/33320_Previsualizacion_122_137lo.jpg[/IMG]

---

### Post by baila0 on 2010-07-13
Bueno, aquí les dejo mi desktop, es bien simple, para optimizar recursos ;)


**Tema:**
Dock: Gnome-Do (docky)
Cursor: PROTOZOA (animado)
Wallpaper: Encontrado por ahí
GTK: Showtime
Icons: The Last Amazing Greys

**Otros:**
Global-Menu
Terminal Integrado en el Escritorio
BURG Theme: black_and_white
Chromium (mucho mas rápido que Firefox)

*** **Dual-boot porque necesito Window$ para algunos programas que no puedo usar en Ubuntu.

---

### Post by Q-cho on 2010-07-30
> **baila0 said:**
> Bueno, aquí les dejo mi desktop, es bien simple, para optimizar recursos ;)


**Tema:**
Dock: Gnome-Do (docky)
Cursor: PROTOZOA (animado)
Wallpaper: Encontrado por ahí
GTK: Showtime
Icons: The Last Amazing Greys

**Otros:**
Global-Menu
Terminal Integrado en el Escritorio
BURG Theme: black_and_white
Chromium (mucho mas rápido que Firefox)

*** **Dual-boot porque necesito Window$ para algunos programas que no puedo usar en Ubuntu.
Hola soy un poco novato en esto y quisiera saber que es y como funciona el dual-boot ¿es diferente al Grub?

---

### Post by Carlos C on 2010-07-30
> **Q-cho said:**
> Hola soy un poco novato en esto y quisiera saber que es y como funciona el dual-boot ¿es diferente al Grub?
Q-cho, hola. Por favor crea un tema nuevo para plantear esas dudas, esta conversación es únicamente para compartir nuestros escritorios. Tus preguntas debes hacerlas en el subforo "Software" y para que no tengas problemas en obtener una respuesta es necesario que leas las siguientes indicaciones:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

Saludos.

---

### Post by Q-cho on 2010-08-01
> **Carlos C said:**
> Q-cho, hola. Por favor crea un tema nuevo para plantear esas dudas, esta conversación es únicamente para compartir nuestros escritorios. Tus preguntas debes hacerlas en el subforo "Software" y para que no tengas problemas en obtener una respuesta es necesario que leas las siguientes indicaciones:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

Saludos.

ok disculpa no quise desordenar el orden del foro pero creia que para que crear un tema nuevo si se puede responder rapidamente la diferencia aveces no tienen que ser tan estrictos por que al final el foro tiene muy poca utilidad si nadie comenta o se mete esta muy poco activo el foro chileno.

---

### Post by Patriciologico on 2010-08-01
> **Q-cho said:**
> no tienen que ser tan estrictos por que al final el foro tiene muy poca utilidad si nadie comenta o se mete esta muy poco activo el foro chileno.

Mantener el orden significa, que las respuestas se encuentran mas rápido, nadie va a buscar que es dual boot en un thread de pantallazos de escritorio. Lo importante es que el foro sea efectivo para resolver las dudas, aunque eso signifique que la gente no comente, pues encontró su respuesta y se fue.

Por ejemplo dual boot esta suficientemente documentado, es el tipo de threads que la gente lee y no comenta. Ej 

[http://es.wikipedia.org/wiki/Dual_boot](http://es.wikipedia.org/wiki/Dual_boot)

[¿Que es dual boot?]("http://www.google.cl/linux?hl=es&q=que+es+dual+boot&btnG=Buscar&meta=lr%3Dlang_es")

---

### Post by baila0 on 2010-08-26
Update...
Mi Desktop al 26 de Agosto 2010

Lucid Lynx obviamente

Emerald: SWAN
GTK: Kuroa 
Covergloobus: Dirty
Iconos: AwOken
Wallpaper: [http://fiftyfootshadows.net/category/desktops/page/15/](http://fiftyfootshadows.net/category/desktops/page/15/)

---

### Post by dierocck on 2010-08-28
> **baila0 said:**
> Update...
Mi Desktop al 26 de Agosto 2010

Lucid Lynx obviamente

podrias dar mas info. sobre tu escritorio, el wallpaper y los iconos que ocupas por ejemplo

---

### Post by baila0 on 2010-08-28
> **dierocck said:**
> podrias dar mas info. sobre tu escritorio, el wallpaper y los iconos que ocupas por ejemplo

Editado en el post con la captura:KS

---

### Post by dierocck on 2010-08-28
> **Superace said:**
> Buenas a todos... soy nuevo en el foro y también en ubuntu. Tengo nociones muy básicas de linux, pero de todas formas intentare ser de ayuda en este foro... y obviamente recibir ayuda de este gran mundo del software libre.

Este es mi escritorio actual:

[IMG]http://i839.photobucket.com/albums/zz315/superace2/33320_Previsualizacion_122_137lo.jpg[/IMG]

Colega, como pedi en el post anterior ojala dejaran mas info. sobre sus escritorios

thanx!

---

### Post by Superace on 2010-08-29
> **dierocck said:**
> Colega, como pedi en el post anterior ojala dejaran mas info. sobre sus escritorios

thanx!


Lamentablemente por intentar actualizar el kde mate este escritorio... pero por lo que recuerdo con respecto a las transparencias las realice con el plasmoid de carpeta escritorio...

---

### Post by xtremox on 2010-10-09
[[img]http://media.static.grupog3cr.com/thumbs/pantallazo.jpg[/img]](http://media.static.grupog3cr.com/?v=pantallazo.jpg)

el mio :D

ubuntu lucid lynx

tema gtk small victory
iconos awoken
font: ubuntu la de 10.10 beta
wall: lo saque de deviantart se llama clouds creo :D
terminal:sakura

---

### Post by Revoltoso on 2010-10-09
[IMG]http://uppix.net/1/b/b/54b7c2bbc3d2d7af249faf399a3e7.jpg[/IMG]

[IMG]http://uppix.net/d/0/5/f6499982b73bc8eddbeadae4e91b8.jpg[/IMG]



Barra: Cairo-Dock
Para tener varios fondos: Desktop Drapes
Tema Ubuntu para Chrome en: [http://gnome-look.org/content/show.php/Ubuntu+Theme+for+google+Chrome++Chromium?content=11660](http://gnome-look.org/content/show.php/Ubuntu+Theme+for+google+Chrome++Chromium?content=11660)

Fondo: IV Region, Pisco Elqui (Con cultivo en terrazas en al final).

---

### Post by moreback on 2010-10-14
Bueno, me pasé hace poco a Lucid Lynx, así que ahí va mi escritorio.

Se ve que estoy quemando un cd al mismo tiempo que tengo abierta una maquina virtual con winvista, el gimp, thunderbird para los correos del trabajo y el dock es Docky.

Saludos.

---

### Post by Killer Jacker on 2010-12-19
Aquí les comparto mis escritorios!!!
Estoy contento porque después de varios intentos le encontré la organización útil (para mí) a más de un escritorio!! Así tengo todo a mano, siempre online y optimizo mi trabajo.
No está muy "tuneado" visualmente, pero logré organizarlo efectivamente.
Saludos!!

Monitor: Dual Monitor Screen 1: 1280 x 800 -  Screen 2: 1920 x 1080
Wallpaper: abstract_0073.jpg (hdwallpapers.net)
Icon Set: Humanity - Dark
Theme: Dust

---

### Post by magicdrums on 2011-01-14
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181076&stc=1&d=1295031650[/IMG]

---

### Post by Patriciologico on 2011-01-15
Minimalista..me gustan los escritorios desocupados. ¿usas Gnome-Do?

---

### Post by patraicio on 2011-04-16
Tipografía: Myriad Pro (algunas con negrita)
Tema: Editado

Controles: Sense
Borde Ventana: Dust
Iconos: nouveXT-1.7
Puntero: whiteglass

Fondo: Jote de Cabeza colorada en vuelo - Valdivia (la foto la saqué yo)
Opera 11.10, fondo marcado rápido: foto X que encontré por ahí.

Saludos!

[IMG]http://files.myopera.com/duckboyInc/albums/375100/01.png[/IMG]

[IMG]http://files.myopera.com/duckboyInc/albums/375100/2.png[/IMG]

[IMG]http://files.myopera.com/duckboyInc/albums/375100/3.png[/IMG]

[IMG]http://files.myopera.com/duckboyInc/albums/375100/4.png[/IMG]

---

### Post by juanuni on 2011-04-17
Aqui va el mio :

/home/juan/Imágenes/Pantallazo-5.png

---

### Post by juanuni on 2011-04-17
Elegant Gnome, conky, cairo dock, compiz fusion.

---

### Post by wapen on 2011-09-22
Aquí va el mio:

[IMG]http://img7.imagebanana.com/img/yw11nq6j/Pantallazo1.png[/IMG]

---

### Post by juanuni on 2011-11-01
Ahi el mio ... 
Emerald : MinimalLittleGlass
gtk: kde42-oxygen
puntero: Turbine

---

