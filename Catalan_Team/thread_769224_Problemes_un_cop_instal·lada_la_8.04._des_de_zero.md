---
title: "Problemes un cop instal·lada la 8.04. des de zero"
date: 2008-04-26
forum: Catalan Team
---

### Post by lo gambusí on 2008-04-26
Salut!

He instal·lat l'Ubuntu 8.04 a un Samsung Core2Duo amb una targeta ATI Radeon 1250 que originàriament anava en vista però ara anava en xp.

Ho he instal·lat amb Alternate, perquè ja vaig intentar instal·lar-lo en lo normal fa un temps i me va ser impossible. 

Un cop instal·lat encenc lo portàtil, i un cop passada la imatge de presentació, lo logotip d'ubuntu en la barra taronja, se'm queda fregit i me diu lo missatge següent: 

> * Starting anac(h)ronistic cron anacron
* Starting deferred execution scheduler atd
* Starting periodic command scheduler crond
* Checking battery state...
* Running local boot scripts (/etc/rc.local) 

Vull aclarir que ja vaig obrir un [fil]("http://ubuntuforums.org/showthread.php?t=630584") prou semblant fa temps, però que en faig un de nou per no haver de fer-vos-ho rellegir tot...

Algú pot ajudar-me?

Moltes gràcies!

PS: espero que haigue anat bé la festa!! :D

---

### Post by kukat on 2008-04-27
Doncs jo anava a escriure un fil semblant, igual es el mateix o paregut,  ja que jo també tinc una Ati Radeon (9550). Vaig fer l'upgrade amb el Alternate i ara l'entorn gràfic ja no es el que era. La resolució de pantalla no és la correcta, els efectes van a trompicons, i ja he provat diverses coses: canviar el fglrx per el "libgl1-mesa-glx" (no se per que, però bé...) configurar altra vegada la pantalla i la gràfica amb "sudo displayconfig-gtk", reinsta&#320;lar el controlador d'ATI...de tot, però segueix sense funcionar correctament. Alguna suggerència? Obric un nou fil millor? :)

Ah! Espere que la festa Ubuntu haja sigut la canya!!:guitar:

---

### Post by Frealof on 2008-04-27
Iep!

Jo tinc una Nvidia GeForce 7300GT... pel tema resolució de pantalla, ho vaig solucionar fent servir l'ENVY.

Salut!

---

### Post by menut on 2008-04-27
Potser us interessa:
> [http://blog.gunbladeiv.com/2008/04/ubuntu-ati-crash-on-hardy-upgrade.html](http://blog.gunbladeiv.com/2008/04/ubuntu-ati-crash-on-hardy-upgrade.html)

---

### Post by gunbladeiv on 2008-04-27
may i know what is the exact problem.. maybe could translate a bit.  Cause i notice my blog being mention here.
:confused:

---

### Post by menut on 2008-04-27
"Lo gambusí" have some problems with a fresh Hardy installation. 

He has an ATI Radeon, and says when Ubuntu is loading, the screen freezes (after "Running local boot scripts (/etc/rc.local)") and he has no way to log in the system.

He did the installation with the hardy alternate cd.

I posted the link to your blog to give him a possible solution.

Sorry for my bad english :)

---

### Post by gunbladeiv on 2008-04-27
So here is the solution that possible to revert the graphic cards:
And I'm going to write this tutorial in english, so i hope someone could translate it into other language if possible: :)

1)  First of all, when the arrive GRUB list option menu, Please choose Safe Mode, so you will be able to login as user/root to repair your graphic settings.

2)  Then we need to reset the xorg.conf to the original state to use "vesa" instead of ATI. To do this, you need to run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
3)  Then you will need to install the 'fglrx' driver for ATI to work properly(You must have internet connection right now).
```
sudo apt-get install linux-restricted-modules-generic restricted-manager xorg-driver-fglrx
```
4)  Then do:
```
sudo depmod -a
```
5)  Then the tricky part is to change the xorg.conf by using text editor of your choice.  So in this tutorial, i will use gedit to make it user friendly:
```
sudo gedit /etc/X11/xorg.conf
```
6)  Search for words like *Driver "mesa"* and change it to *Driver "fglrx"* .
7)  Then we need to check the configuration for any errors by :
```
sudo aticonfig --initial -f
```
8)  Last please reboot, and login as usual.

I hope this could settle your problem.  Cuz I do have the same problem once and i did this steps to get rid of the errors and now running smooth with my fglrx driver for ATI.

---

### Post by menut on 2008-04-27
TRADUCCIÓ:

1)Primer de tot, escull la opció "mode segur" del GRUB per poder iniciar sessió com a root i reparar la configuració gràfica. (Comentari meu: suposo que s'ha volgut referir al mode recuperació)

2)Després necessitem resetejar el xorg.conf, per a poder utilitzar "vesa" enlloc de ATI. Per a fer-ho, escriu:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

3)Després necessitaràs instal·lar el driver "fglrx" d'ATI per que funcioni correctament (necessites estar connectat a internet, ara)

```
sudo apt-get install linux-restricted-modules-generic restricted-manager xorg-driver-fglrx
```
4) Després fés:

```
sudo depmod -a
```

5)Després, la part difícil és canviar el xorg.conf utilitzant l'editor de textos que vulguis. En aquest tutorial, usaré gedit per a fer-ho "amigable":

```
sudo gedit /etc/X11/xorg.conf
```

6)Busca les paraules, alguna cosa semblant a Driver "mesa", i canvia-ho per Driver "fglrx".

7)Ara necessitem revisar els possibles errors de la configuració amb:

```
sudo aticonfig --initial -f
```
Per últim, reinicia i entra a la sessió, com sempre s'ha fet.


Espero que això et sol·lucioni el problema. Jo el tenia i amb aquestes passes m'he desfet dels errors i ara em funciona sense entrebancs, amb el driver fglrx per a ATI.

---

### Post by gunbladeiv on 2008-04-28
thanks for the translation. 
you all rawks:guitar:

---

### Post by kukat on 2008-04-28
Thanks!
Gràcies!
Pareix que ja vaja bé! 
La veritat es que ha sigut un poc estrany, ja que algunes coses de les que deieu que tenia que fer, ja estaven fetes...deu ser que faltava algun paquet o jo ke se.....bé, la questio es que ja tinc l'ordinador com abans....
Ah! En l'opció "Afegeix al Quadre" heu vist les opcions que hi ha? molt intereseants!! :) Sobretot la de "Força la sortida d'una aplicacio..." a pesar de no gastar-la quasi mai..jejeje

---

### Post by kukat on 2008-04-28
He tornat a encendre l'ordinador, i hem torna a anar igual de malament que abans!!!!:confused: No ho entenc! si anava molt bé!! li he ficat el AWN, he activat tranquilament els efectes, li he afegit els applets del AWN, he instalat el Kdenlive, que no l'encontrava (??) i quan he reiniciat, m'ha sortit un altra vegada la pantalleta per configurar la pantalla i la gràfica........

El meu xorg.conf, es aquest....

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:1"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"800x600@85"	"800x600@60"	"800x600@75"	"832x624@75"	"800x600@72"	"1024x768@85"	"800x600@56"	"1024x768@75"	"640x480@85"	"1024x768@70"	"640x480@75"	"1024x768@60"	"640x480@72"	"1024x768@43"	"640x480@60"	"1152x864@75"	"1280x960@60"	"1280x1024@60"	"1400x1050@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1400x1050@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection


Que pot passar???? Estic confós! amb el Gutsy Gibbon no hi havia problema......

---

### Post by lo gambusí on 2008-04-29
Kukat, crec que hauries d'haver obert un altre fil, perquè ara mos embolicarem...

Jo em quedo al segon pas, em diu > could not resolve es.archive.ubuntu.com.

Estic connectat a Internet per cable.

---

### Post by menut on 2008-04-29
Canvia de servidor.

Vés a Sistema > Administració > Fonts de programari i escull el servidor que vulguis (El servidor principal sol anar bé).

---

### Post by kukat on 2008-04-29
Tens raó, en obric un de nou, per que si no s'embolicarem..jejej:)

---

### Post by lo gambusí on 2008-04-29
no puc entrar a l'entorn gràfic, eh...

ai que estem parlant de coses diferents:?

tot això ho he fet entrant des del grup a recovery mode, i a la pantalla que em surt al carregar-se, que em deixa triar entre resume, root i xfix he triat root. llavors simplement em surt una línia de text on puc escriure, com a root.

és una altra cosa lo que he de fer?

---

### Post by menut on 2008-04-29
Edita el /etc/apt/sources.list amb un editor de text que funcioni amb el terminal, per exemple, nano:

> nano /etc/apt/sources.list

On vegis es.archive.ubuntu.com, canvia-ho per archive.ubuntu.com i desa els canvis.

---

### Post by lo gambusí on 2008-04-30
moltes gràcies... no podré comprovar com va fins dilluns, però ja aniré explicant.

salut!

---

### Post by lo gambusí on 2008-05-06
Sé que és una pregunta ridícula... però com deso els canvis amb nano?:?

---

### Post by Neret on 2008-05-06
ctrl+o 
Abaix del nano tens totes les dreceres.
Apasiau

---

### Post by lo gambusí on 2008-05-06
Gràcies, Neret.

Canviat això, faig 
> sudo apt-get install linux-restricted-modules-generic restricted-manager xorg-driver-fglrxi me diu:
> E: Couldn't find package xorg-driver-fglrx :?

---

### Post by pespin on 2008-05-06
fes un "sudo aptitude update" per a que descarregui els indexs de paquets disponibles als repositoris i ja te'l trobarà :)

---

### Post by lo gambusí on 2008-05-06
> Could not resolve archive.ubuntu.com
Could not resolve security.ubuntu.com

És com si no tingués connexió... :?

---

### Post by lo gambusí on 2008-05-06
Ara estava pensant...

Estic connectat a Internet via cable a la connexió de la UAB. Esta connexió a vegades (depèn com li pega, la veritat) demana nom d'usuari i contrassenya.

Podria ser que no me connectés per això? Hi ha alguna manera d'identificar-me per la consola? O de descarregar l'arxiu des d'un altre ordinador i instal·lar-lo via llapis USB?

aix...

---

### Post by pespin on 2008-05-06
Loguejar-te a la wifi suposo que deu haver-hi alguna ordre pero la desconnec, ja que no uso wifi :) Sino pots posar la informaciño en algun fitxer diria

I per saber si tens internet tan fàcil com fer un "ping" i mirar si retorna ;)

---

### Post by lo gambusí on 2008-05-06
Li he dit "ping" i me diu:> [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
[-p pattern] [-s packetsize] [-t ttl] [-] interface or address]
[-M mtu discovery hint] [-S sndbuf]
[ -T timestamp option ] [ -Q tos] [hop1 ---] destination
No entenc res xD

---

### Post by pespin on 2008-05-06
Informació sobre el ping: [http://ca.wikipedia.org/wiki/Ping](http://ca.wikipedia.org/wiki/Ping)

El ping l'has de fer contra una màquina, per exemple "ping www.google.com". El ping anirà enviant paquets a l'adreça especificada fins que premis CTRL+C. Si en enviar paquets et posa que el servidor et respon, vol dir que estàs connectat a internet :)

---

### Post by lo gambusí on 2008-05-06
> ping: unknow host [www.google.com](www.google.com):?

---

### Post by pespin on 2008-05-06
Això vol dir que no pot transofrmar el domini en IP, i per tant que no tens accès als servidors DNS -> no tens internet.

---

### Post by lo gambusí on 2008-05-06
Festival xD

Puc instal·lar l'arxiu des d'un USB o alguna cosa així?

---

### Post by lo gambusí on 2008-05-07
He descarregat l'arxiu, des d'[aquí]("http://packages.ubuntu.com/dapper/i386/xorg-driver-fglrx/download"), i ara vull instal·lar-lo des d'un usb. Faig > cd /media/KINGSTON_ (perquè és lo nom en lo qual me surt l'usb al meu ordinador) i me diu > bash: cd: KINGSTON: No such file or directory.

Què faig malament? Alguna idea? :?

---

