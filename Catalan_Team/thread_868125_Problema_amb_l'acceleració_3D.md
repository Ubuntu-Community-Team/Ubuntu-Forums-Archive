---
title: "Problema amb l'acceleració 3D"
date: 2008-07-23
forum: Catalan Team
---

### Post by alhanduin on 2008-07-23
Bones!! 

Ja havia entrat en varies ocasions en aquest forum i gràcies a vosaltres he resolt molts dels meus dubtes, i ara us torno a necessitar... Resulta que tinc un problema amb l'acceleració 3D del meu Acer que porta una tarjeta ATI Radeon 9600/9700 amb una memòria de 64mb. Sempre he tingut problemes amb ella però ni amb la última versió d'ubuntu he aconseguit que corri bé... He probat moltes coses però cap fructífera, la última que he provat és el programa envyng que t'instala directament els paquets. He llegit que és un dels sistemes més efectius però tampoc em funciona... No puc posar ni els efectes visuals normals ja que em salta una pantalla blanca i el linux es queda penjadíssim i és clar, necessito fer còrrer el 3D max i és impossible...

Ja sé que és un tema molt repetit però abans d'esciure aquest post he probat molt...Així que si hi ha algú que hagi pogut configurar bé aquesta tarjeta i em pugui guiar (penseu que sóc principiantet eeeeeee!!!) li estaria molt agrait.

Moltes gràcies pel vostre temps. Albert

---

### Post by quitus on 2008-07-23
jo tenia una ati radeon 9200se 128MB i amb el hardy tenia acceleració 3d sense haver de tocar res, penso que la teva targeta te poca memòria per tenir capacitat 3d.

salut.

---

### Post by alhanduin on 2008-07-23
Gràcies per la teva resposta Marc... Però no crec que sigui ben bé això que tu em comentes ja que aquest ordenador va estar corrent durant 2 anys en XP i per dir-te un exemple jo podia jugar a jocs que ara queden totalment bloquejats, a ratlles... El tema del 3D max no t'ho puc dir xq no el vaig probar d'usar...

---

### Post by papapep on 2008-07-23
Has provat a instal·lar directament el controlador que proporciona ATI?

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-7-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-7-x86.x86_64.run)

---

### Post by alhanduin on 2008-07-23
En la versió de guttsy Gibbon ho vaig probar seguint una "guia" que vaig trobar xl foro llatí, però em va donar molts problemes al fer-ho i després de probar molt i haver de reinstalar l'ubuntu varies vegades, quan em va semblar que ho havia aconseguit seguia tenint els mateixos problemes...

També he probat d'anar a sistema, administración, controladores de hardware, instalar controlador para tarjetas gràficas ATI, xo tampoc em va resultar...

Ara, després d'haver instalat l'envy ng, em va aparèixer un programa anomenat ATI catalyst control center... xo tp funciona...

Xq et facis una idea, no puc obrir ni el google earth per a linux, i començo a estar desesperadet! jejejejej

---

### Post by alhanduin on 2008-07-23
He decidit que tornaré a començar i seguiré al pau de la lletra la guia de l'ubuntu;

1.- Primer pas;

alhanduin@Tostadora:~$ lspci -nn | grep VGA 
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50] 

X tant és una placa en la que l'acceleració 3D està suportada en els drivers lliures.

2.- Elimino els drivers d'ATI propietaris ( fglrx );

alhanduin@Tostadora:~$ sudo apt-get remove --purge xorg-driver-fglrx


3.- Comprovo la versió de la llibreria libGL.so (en /usr/lib) instalada pel xorg-driver-fglrx;

alhanduin@Tostadora:~$ glxinfo |grep vendor
server glx vendor string: SGI
**client glx vendor string: SGI**
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

La guía diu que aquí hauria de posar ATI enlloc de SGI!!! Algú sap com ho puc fer???


4.- Reinstal.lar els paquets libgl1 -mesa -glx i dri;

alhanduin@Tostadora:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

Leyendo lista de paquetes... Hecho

Creando árbol de dependencias       

Leyendo la información de estado... Hecho

0 actualizados, 0 se instalarán, 2 reinstalados, 0 para eliminar y 0 no actualizados.

Necesito descargar 13,3MB de archivos.

Se utilizarán 0B de espacio de disco adicional después de desempaquetar.

¿Desea continuar [S/n]? s

Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libgl1-mesa-glx 7.0.3~rc2-1ubuntu3 [151kB]

Des:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libgl1-mesa-dri 7.0.3~rc2-1ubuntu3 [13,2MB]

Descargados 13,3MB en 42s (315kB/s)                                            

(Leyendo la base de datos ...  

158606 ficheros y directorios instalados actualmente.)

Preparando para reemplazar libgl1-mesa-glx 7.0.3~rc2-1ubuntu3 (usando .../libgl1-mesa-glx_7.0.3~rc2-1ubuntu3_i386.deb) ...

Desempaquetando el reemplazo de libgl1-mesa-glx ...

Preparando para reemplazar libgl1-mesa-dri 7.0.3~rc2-1ubuntu3 (usando .../libgl1-mesa-dri_7.0.3~rc2-1ubuntu3_i386.deb) ...

Desempaquetando el reemplazo de libgl1-mesa-dri ...

Configurando libgl1-mesa-glx (7.0.3~rc2-1ubuntu3) ...

Configurando libgl1-mesa-dri (7.0.3~rc2-1ubuntu3) ...

Processing triggers for libc6 ...

ldconfig deferred processing now taking place


5.- Configurar l'arxiu xorg.conf;

alhanduin@Tostadora:~$ sudo vim /etc/X11/xorg.conf (enlloc de vim també podem usar nano, gedit o kate)

He canviat la secció &#8220;device&#8221; i hi he escrit;
Section "Device"

	Identifier	"Radeon 9600"

	Driver		"ati"

	BusID           	"PCI:1:0:0"

	Option          	"XAANoOffscreenPixmaps"

	Option		"VideoOverlay"	"on"

	Option		"OpenGLOverlay"	"off"

EndSection

És necessari els últims 2 options??? algú em pot dir xq serveixen cadascún??? (és que ja els tenia i no els he volgut esborrar però no en tinc ni idea de si els necessito o no)

He canviat la secció &#8220;Monitor&#8221;;

Abans tenia; 
Section "Monitor"

	Identifier	"Configured Monitor"
EndSection

Ara he posat;
Section "Monitor"

	Identifier      	"Generic Monitor"

	Option          	"DPMS"

	HorizSync       28-72

	VertRefresh     43-60

EndSection

He fet bé posant el &#8220;DPMS&#8221;?? Com sabré si m'està funcionant bé o no?

He canviat la secció &#8220;Monitor&#8221;; 

Abans tenia;
Section "Screen"

	Identifier	"Default Screen"

	Monitor	"Configured Monitor"

	Device		"Configured Video Device"

	Defaultdepth	24

EndSection

Ara he posat;
Section "Screen"

	Identifier      "Default Screen"

	Device          "Radeon 9600"

	Monitor         "Generic Monitor"

	DefaultDepth    24

SubSection "Display"

	Depth           24

        	Modes          "1280x800" "1024x768"
	Virtual	"1024x768"
EndSubSection

EndSection

He canviat la secció &#8220;ServerLayout&#8221;; 

Abans tenia;
Section "ServerLayout"

	Identifier	"Default Layout"

  	screen "Default Screen"

	Inputdevice	"Synaptics Touchpad"

EndSection

Ara tinc;
Section "ServerLayout"

        Option          "AIGLX"         "true"

	Identifier      "Default Layout"

	Screen          "Default Screen"

	InputDevice     "Generic Keyboard"

	InputDevice     "Configured Mouse"

	Inputdevice	"Synaptics Touchpad"

EndSection

Al final del document he afegit; 
Section "DRI"
	Mode 0666
EndSection

El document Xorg.conf ha quedat de la segïuent manera; 


Section "Screen"

	Identifier      "Default Screen"

	Device          "Radeon 9600"

        Monitor         "Generic Monitor"

        DefaultDepth    24

SubSection "Display"

	Depth           24

        Modes           "1280x800" "1024x768"

	Virtual		"1024x768"

EndSubSection

EndSection



Section "Device"

	Identifier	"Radeon 9600"

	Driver		"ati"

	BusID           "PCI:1:0:0"

        Option          "XAANoOffscreenPixmaps"

	Option		"VideoOverlay"	"on"

	Option		"OpenGLOverlay"	"off"

EndSection



Section "InputDevice"

	Identifier	"Generic Keyboard"

	Driver		"kbd"

	Option		"XkbRules"	"xorg"

	Option		"XkbModel"	"pc105"

	Option		"XkbLayout"	"es"

EndSection



Section "InputDevice"

	Identifier	"Configured Mouse"

	Driver		"mouse"

	Option		"CorePointer"

EndSection



Section "InputDevice"

	Identifier	"Synaptics Touchpad"

	Driver		"synaptics"

	Option		"SendCoreEvents"	"true"

	Option		"Device"	"/dev/psaux"

	Option		"Protocol"	"auto-dev"

	Option		"HorizEdgeScroll"	"0"

EndSection



Section "ServerLayout"

        Option          "AIGLX"         "true"

	Identifier      "Default Layout"

	Screen          "Default Screen"

	InputDevice     "Generic Keyboard"

	InputDevice     "Configured Mouse"

	Inputdevice	"Synaptics Touchpad"

EndSection



Section "Monitor"

	Identifier     	"Generic Monitor"

	Option         	"DPMS"

	HorizSync       28-72

	VertRefresh     43-60

EndSection



Section "Extensions"

	Option		"Composite"	"Enable"

EndSection



Section "DRI"

        Mode 0666

EndSection

---

### Post by orestesmas on 2008-07-23
> **alhanduin said:**
> 

2.- Elimino els drivers d'ATI propietaris ( fglrx );

alhanduin@Tostadora:~$ sudo apt-get remove --purge xorg-driver-fglrx


No sé si pot ser això però a continuació cal descarregar els mòduls del nucli que ha posat el controlador privatiu, perquè altrament no es podran carregar els mòduls del controlador lliure. Usa rmmod si saps fer-ho, però si te'n vols assegurar, rebota la màquina.

Aquest és un tema que a mi m'havia donat força maldecaps en el passat.

---

### Post by alhanduin on 2008-07-24
Ostres a mí me n'està donant moltíssims de maldecaps!!! Obviament quan vaig acabar tot el procés que deia a la guia i vaig reiniciar l'ordenador, l'ubuntu em va començar a dir que no reconeixia la tarjta gràfica (aixó desde la consola, abans d'obrir-se la part gràfica del SO) i ja no he tornat a poder fer còrrer l'ubuntu de cap manera... Quan intento entrar a ubuntu aquest es queda congelat a la pantalla d'introducció del nom d'usuari i contrassenya i comencen a aparèixer ratlles, quadrats... 

Sempre que he intentat arreglar-ho he hagut de tornar a instalar l'ubuntu... pèrò aquesta versió no la vull reinstalar xq durant la instal.lació s'em congela i només la vaig aconseguir instalar al cap de rebotar l'ordinador unes 20 vegades... Així que algú sap com ho puc fer x recuperar l'ubuntu??? 

Com podria entrar i tornar a canviar l'Xorg.conf??? O això no funcionaria???

Aquest tema em comença a tenir moooolt cremat!!!!

Moltes gràcies a tothom!!

---

### Post by papapep on 2008-07-24
Jo no vull ser insistent, però provaria amb el controlador (tancat, privatiu i asquerós) que proporciona el fabricant al seu lloc web. No és un procés complicat, poc més que executar, enter, enter...).

---

### Post by alhanduin on 2008-07-24
Okis papappep probaré el que tu dius. Peró primer em podries ajudar a recuperar l'ubuntu sense reinstalarlo??? O això que em dius ho puc probar desde fora sense necessitat d'entrar a la part gràfica del SO???

Moltes gràcies per adelantat

---

### Post by papapep on 2008-07-24
Si no recordo malament, i per lògica, l'instal·lador es pot fer servir sense entorn gràfic. Prova-ho i veuràs si sí, o si no.

---

### Post by alhanduin on 2008-07-24
mmmm jo diria que no xq quan poso el cd i selecciono instalar ubuntu em crea directament un entorn gràfic sense que jo pugui escollir...

---

### Post by alhanduin on 2008-07-24
Bueno tornaré a carregar l'ubuntu... l'he posat en modo grafico seguro i sembla que així sí que anirà, però tinc u problema amb les particions. Jo tinc 3 particions

17Gb x al ubuntu
40Gb x a disc dur de seguretat
2Gb d'area d'intercanvi

Ara a la instalació em diu que posi el punt de muntatge i tot aixó. Si jo no vull eliminar el contingut dels 40Gb el que he de fer és el següent??

17Gb formatear y montar en /
40Gb No formatear y montar en /home
2gb

---

### Post by alhanduin on 2008-07-24
Ja està! Linux nou... Ara estic obert a les vostres idees de com arreglar l'acceleració 3D

---

### Post by alhanduin on 2008-07-25
He instalat els drivers privatius que em deia linux (sistema --> administración --> controladores del hardware) i així tampoc m'ha funcionat... Es queda penjat quan he d'usar 3D.

Què més puc fer?

---

### Post by papapep on 2008-07-25
El que et vaig comentar al post #4 d'aquest mateix fil :-)

[http://ubuntuforums.org/showpost.php?p=5444916&postcount=4](http://ubuntuforums.org/showpost.php?p=5444916&postcount=4)

---

### Post by alhanduin on 2008-07-25
Okis instalaré aquests drivers a veure què tal... Però abans he d'esborrar alguna cosa?

---

### Post by ffp on 2008-07-26
Hola,
Jo tinc una ATI 9600, i ja he passat per molts embolics, quan vaig actualitzar a Hardy, tots els embolics de configuracions fetes per la gràfica van fer que funciones fatal. Solució, reinstal·lació nova i neta, i Envy (envyng) via Synaptic, no es cap meravella i el driver actual es el 8.1 crec (res del 8.7 actual). Acceleració raonable i fins hi tot google earth (i alguna penjada de tant en tant).
Amb Feisty vaig provar l'instal·lació manual del driver privatiu i tot i que em va costar, vaig conseguir que em funcionés, però perden tantes hores que ara no m'ho penso massa, Envy.
Nota: el driver privatiu que està a synaptic es antediluvià i no suporta acceleració gràfica.

Pot ser que no t'ajudi gaire, ho sento, la 9600 es la pitjor gràfica que he tingut, l'anterior una ATI 9250, nomes accepta drivers lliures i funciona la mar de bé, al ordinador vell que tinc per fer "experiments" linuxeros.

EDITO: donat que has fet una instal·lació neta, lo que crec que hauries de fer es:
Desinstal·lar el driver privatiu (inhabilitar el driver, sistema, administració, controladors de maquinari).
Per synaptic instal·lar envyng-core i envyng-gtk.
Una vegada instal·lat, aplicacions, eines del sistema, enviNG
Instal·la el controlador per a ATI (instal·lació automàtica).
Mes informació a [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Sort !!

---

