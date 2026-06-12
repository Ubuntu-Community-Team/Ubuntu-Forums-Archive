---
title: "Instal·lar paquets tar.bz2 i tar.gz"
date: 2008-09-15
forum: Catalan Team
---

### Post by panicot on 2008-09-15
què he de fer per instala el programes baixats de internet?

---

### Post by kukat on 2008-09-15
quin programa vols instal.lar?  a "Aplicacions", "Afegeix/Elimina", tens moltíssims programes per instalar solament tens que "activar la V" i "aplicar els canvis" 
tambe pots instal.lar programs a "Sistema" "Administració" "Gestor de Paquets Synaptic"
o a la consola amb "sudo apt-get install" o "sudo aptitude install" i el programa que vols instalar....també sol funcionar.

Però la pregunta és poc específica.......

Benvingut!

---

### Post by papapep on 2008-09-15
Panicot, benvingut al fòrum. Crec que et seria de profit fer una bona llegida al [fil per als nouvinguts]("http://ubuntuforums.org/showthread.php?t=599965"), tal i com apunta el contingut de la resposta d'en Kukat ;-)

---

### Post by panicot on 2008-09-15
jo voldria saber com instalar els programes descarregats de internet que normalment son.tar.bz2

els programes que no s'han de baixar ja els se instalar

---

### Post by kukat on 2008-09-15
normalment vindrà amb un readme que ho explica...però quasi sempre és...
en la consola:
cd carpetadescomprimida
./configure
make
make install

però també depén de quin programa es el que vajes a instal.lar!!!

---

### Post by panicot on 2008-09-15
gracis

---

### Post by panicot on 2008-09-15
ara tinc un altre problema

que poso cd i el nom de la carpeta descomprimida en aquest cas flock em poso aixo: bash: cd: flock: No such file or directory
i no em deixa continuar amb la instalació

algu em sabria dir com arreglar el problema?

gracias

---

### Post by kukat on 2008-09-15
mira primer amb el comandament:
**ls**
si està en eixe directori la carpeta en questió!!
si la tens en l'escriptori, primer tindràs que fer:
 
**cd Escriptori **

i després:

**cd flock**

i vigila les majúscules i les minúscules sigen iguals!

---

### Post by panicot on 2008-09-16
d'acord

pero despres de fer el cd flock poso ./configure i em posa:bash: ./configure: No such file or directory

que he de fer?

---

### Post by RainCT on 2008-09-16
Benvingut!

Buscant "flock ubuntu" la primera entrada que surt, [Install Flock On Ubuntu](http://brentroos.com/2006/07/24/install-flock-on-ubuntu/), ho explica perfectament (l'excusa de l'anglès no val, tot el que diu és copiar i enganxar :)).

A més, com diu en kukat, a Sistema -> Administració -> Gestor de paquets Synaptic tens milers de programes llestos per ser insta&#320;lats/desinsta&#320;lats amb un clic i amb actualitzacions de seguretat automàtiques. Et recomano que sempre que sigui possible utilitzis el que hi hagi allà, tant per evitar problemes com per estar segur que no insta&#320;les coses "perilloses" (i en cas que no hi sigui però que puguis trobar un .deb també és preferible aquest per la facilitat que et dóna a l'hora d'insta&#320;lat/desinsta&#320;lar/actualitzar).

---

### Post by lpargemi on 2010-08-27
Hola, 

Desenterro un tema antic perquè no he sabut trobar la resposta enlloc. Em passa exactament el mateix que diu sempre que vull instal·lar un tarball d'aquests. La resposta de què al synaptic hi ha moltes coses no em serveix... vull instal·lar un tarball. 

I sempre passa el mateix: 

```
lluis@lluis:~/Downloads/CarpetaDelPrograma$ ./configure
bash: ./configure: No such file or directory

```

Primera pregunta: On es suposa que s'hauria de descomprimir un paquet tarball? 
Segona pregunta: Què es suposa que estic demanant amb això?

Agraït

Lluís

---

### Post by wgarcia on 2010-08-29
El primer que hauries de fer es "desempaquetar" aquests paquets en qualsevol directori on tinguis espai suficient i permisos de lectura i escriptura (el teu "home" o "tmp" per exemple). Per desempaquetar els que acaben "tar.gz" o "tgz" (que estan comprimits amb gzip i empaquetats amb "tar") la instrucció és:

tar xzvf paquet.tar.gz 

tar xzvf paquet.tgz

(les opcions: "x" extrau, "z" diu que es gzip, "v" no és estrictament necessari però t'ensenya els arxius que extrau i "f" li diu que ho faci amb el fitxer que ve a continuació). 

Si en canvi l'arxiu és "bz2" llavors substitueix la "z" per una "j":

tar xjvf paquet.tar.bz2

---

### Post by lpargemi on 2010-08-29
> El primer que hauries de fer es "desempaquetar" aquests paquets en qualsevol directori on tinguis espai suficient i permisos de lectura i escriptura (el teu "home" o "tmp" per exemple).
No m'he explicat massa bé, però això ja està fet.
Desempaqueto el tarball en un directori (per exemple el Download), i crea un arbre de carpetes amb tot de fitxers. Salto dins, i faig això del ./configure. I no fa mai res.

Lluís

---

### Post by wgarcia on 2010-08-30
Quan fas això de "./configure" el que estàs fent és cridar l'execució d'un arxiu de comandes (script) que es diu justament "configure" i que hauria de ser-hi a la carpeta on, com tu dius, "saltes". 

Què hi ha a aquesta carpeta on saltes? (fent "ls" des de la línia de comandes un cop has saltat).

---

### Post by lpargemi on 2010-08-31
Gràcies per la pista, ara almenys ja sé què és això del ./configure

En aquest cas no hi ha cap fitxer que es digui així. En aquest cas concret -el digikam- hi ha:
```
lluis@lluis:~/Downloads/digikam-1.4.0$ ls -l
total 4220
-rw-r--r--  1 lluis lluis    7753 2010-08-22 10:53 AUTHORS
-rw-r--r--  1 lluis lluis 3954382 2010-08-22 10:53 ChangeLog
drwxr-xr-x  4 lluis lluis    4096 2010-08-22 10:59 cmake
-rw-r--r--  1 lluis lluis   11244 2010-08-31 20:08 CMakeCache.txt
drwxr-xr-x  5 lluis lluis    4096 2010-08-31 20:02 CMakeFiles
-rw-r--r--  1 lluis lluis   70114 2010-08-22 10:59 CMakeLists.txt
-rw-r--r--  1 lluis lluis    1200 2010-08-22 10:53 config-digikam.h.cmake
-rw-r--r--  1 lluis lluis   18011 2010-08-22 10:53 COPYING
-rw-r--r--  1 lluis lluis   20403 2010-08-22 10:53 COPYING.DOC
-rw-r--r--  1 lluis lluis   26527 2010-08-22 10:53 COPYING.LIB
drwxr-xr-x  7 lluis lluis    4096 2010-08-22 10:59 data
drwxr-xr-x  2 lluis lluis    4096 2010-08-22 10:59 databaseserver
-rw-r--r--  1 lluis lluis      10 2010-08-27 18:40 description-pak
-rw-r--r--  1 lluis lluis     911 2010-08-22 10:53 DESIGN
drwxr-xr-x  2 lluis lluis   12288 2010-08-22 10:59 digikam
-rw-r--r--  1 lluis lluis    1193 2010-08-22 10:53 digikam.lsm.cmake
drwxr-xr-x  2 lluis lluis    4096 2010-08-27 18:39 doc-pak
-rw-r--r--  1 lluis lluis   64333 2010-08-22 10:53 Doxyfile.cmake
-rw-r--r--  1 lluis lluis   13466 2010-08-22 10:53 HACKING
drwxr-xr-x  7 lluis lluis    4096 2010-08-22 10:59 imageplugins
-rw-r--r--  1 lluis lluis      87 2010-08-22 10:53 INSTALL
drwxr-xr-x  2 lluis lluis    4096 2010-08-22 10:59 kioslave
drwxr-xr-x 16 lluis lluis    4096 2010-08-22 10:59 libs
-rw-r--r--  1 lluis lluis     101 2010-08-22 10:53 Mainpage.dox
-rwxr-xr-x  1 lluis lluis     231 2010-08-22 10:53 Messages.sh
-rw-r--r--  1 lluis lluis    2192 2010-08-22 10:53 NEWS
drwxr-xr-x 54 lluis lluis    4096 2010-08-22 10:59 po
-rw-r--r--  1 lluis lluis    7026 2010-08-22 10:53 README
drwxr-xr-x  3 lluis lluis    4096 2010-08-22 10:59 showfoto
drwxr-xr-x  2 lluis lluis    4096 2010-08-22 10:59 themedesigner
-rw-r--r--  1 lluis lluis    6382 2010-08-22 10:53 tips
-rw-r--r--  1 lluis lluis    3226 2010-08-22 10:53 TODO
-rw-r--r--  1 lluis lluis    2607 2010-08-22 10:53 TODO.MYSQLPORT
drwxr-xr-x 19 lluis lluis    4096 2010-08-22 10:59 utilities

```

Al fitxer README hi diu que faci una sèrie de coses i que faci córrer un programa que es diu cmake. Ho faig, el faig córrer -el tinc instal·lat- i em falla. Em penso que al README hi ha una llista dependències que cal seguir quan tingui una estona llarga, i hi deu faltar alguna cosa.

Però això és el meu cas particular. Pel què entenc pel cas genèric: això del ./configure no funcionarà mai si al directori descomprimit del tarball no hi ha el fitxer configure. Aquesta dada no la havia sabut trobar enlloc.

Agraït

Lluís

---

### Post by wgarcia on 2010-09-01
Aquest paquet utilitza el "cmake", que funcionam una mica diferent de com funciona el ".configure". Llegeix el que posa al fitxer "INSTALL", aquí t'explicarà què fer. Normalment creant una carpeta que es digui "build", a aquesta mateixa carpeta on has descomprimit tot:

mkdir build

Entrar a aquesta carpeta:

cd build

Fent:
cmake ../

I finalment:
make

Per instal·lar:
sudo make install

Has de tenir instal·lat el paquet "cmake" òbviament, i segurament "build-essentials". Potser et demani alguna altra cosa a la compilació.

---

### Post by lpargemi on 2010-09-02
Hola. 

Ja tinc instal·lat el cmake. l'executo i em dona un error, com dient que cal KDE4. Tinc instal·lades coses de KDE4, però la màquina corre en ubuntu, és a dir gnome...

```
CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/lluis/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:127 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!

```

I al fitxer CmakeLists.txt, a la línia 127 hi diu

```
FIND_PACKAGE(KDE4 REQUIRED)
```


Al fitxer INSTALL només et diuen que vagis aquí, [http://techbase.kde.org/Getting_Started/Build/KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4) , però la pàgina aquesta és tremenda: hi ha na sèrie incabable d'advertiments que a mi, que no me'n surto amb un suposadament simple ./configure, em dissuadeixen de tot.

Començo a tenir la sospita que aquesta versió de Digikam de moment no anirà sobre la meva màquina...

Agraït

Lluís

---

### Post by kimet on 2010-09-02
Si et compliques la vida per plaer, res a dir. Però si no...busca als repositoris. [http://packages.ubuntu.com/search?keywords=Digikam&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=Digikam&searchon=names&suite=all&section=all)

Salut

---

### Post by wgarcia on 2010-09-03
D'acord amb kukat que digikam és als repositoris, però suposo que si l'estàs compilant alguna raó hi haurà. 

No posa els requeriments a algun fitxer de l'arbre (un INSTALL a la carpeta inicial, per exemple)? 

Potser amb 

sudo apt-get install qt3-assistant qt4-designer qt4-qtconfig qt4-dev-tools

et sigui suficient i no hagis d'instal·lat tot l'escriptori kde. Una altra possibilitat és instal·lar "kde-desktop", compilar, i després desintal·lar "kde-desktop" si no t'interessa. No hi ha problema per tenir el sistema amb els dos escriptoris.

---

### Post by lpargemi on 2010-09-05
Hola.
> Si et compliques la vida per plaer, res a dir.
Efectivament tens raó parcialment. Fa temps que faig anar Ubuntu i vull saber compilar coses ni que sigui per saber-ne.
> D'acord amb kukat que digikam és als repositoris, però suposo que si l'estàs compilant alguna raó hi haurà. 
També tens raó. El problema és que no em funciona el passi de diapositives avançat. Sí que va, però no el puc guardar, i aleshores perquè la matada de fer una passi triant i ordenant fotos i posant música, que es morirà quan tanqui el programa? Vaig demanar ajuda a la llista de correu, i l'únic que vaig aconseguir és solidaritat (algú que tenia el mateix problema). Per tirar endavant vaig provar amb la darrera versió de digikam la 1.4 que no he aconseguit encara instal·lar. (als repositoris hi ha la 1.2) 

De qualsevol manera que aquest post derivi en la instal·lació del digikam 1.4 no era la meva pretensió. Jo només volia saber perquè allò tan bonic que surt a tot arreu quan demanes per instal·lar un tarball (el ./configure, make, etc...)no em funcionava, i això ja ho he aclarit... perquè només va així en el millor des casos. 

Potser cal obrir un post monogràfic de com configurar en particular el digikam...

Agraït pels vostres comentaris

Lluís

---

### Post by kimet on 2010-09-05
No hi ha una única manera de instal·lar un tarball, tar es només un format de compressió. Les instruccions per instalar-lo te les ha de donar el qui l'ha creat. Quasi sempre estan detallades en un fitxer de text a la carpeta del programa, INSTALL.TXT, README.TXT etc. i també t'informarà de les dependències.

Pd. jo vaig fer servir 'imagination' per fer una presentació de diapositives, no sé si et podria ser útil.

Ale adéu.

---

### Post by cafedescafeinat on 2011-04-22
tinc la tarda ben entretinguda.

Busco i busco i la veritat és que em sento ja una mica pallús i em veig obligat a demanar ajuda. És el primer programa que compilo o instal.lo, com es digui. I no puc avançar més... Vosaltres que sou més pro en el tema, em podríeu donar un cop de mà?
[U]
1) llegeixo les instruccions del programa (GDM)
[/U]
The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.


_2) doncs fem el que ens diuen:_
cafedescafeinat@cafedescafeinat-OptiPlex-GX270:~/Escriptori$ **sudo su**
[sudo] password for cafedescafeinat: 
root@cafedescafeinat-OptiPlex-GX270:/home/cafedescafeinat/Escriptori# **ls**
gdm-2.6.0.7.tar.bz2
root@cafedescafeinat-OptiPlex-GX270:/home/cafedescafeinat/Escriptori# **tar -xjvf gdm-2.6.0.7.tar.bz2**
gdm-2.6.0.7/config/Default.in
gdm-2.6.0.7/config/Makefile.am
gdm-2.6.0.7/config/Makefile.in
gdm-2.6.0.7/config/PostSession.in
gdm-2.6.0.7/config/PreSession.in
gdm-2.6.0.7/config/Xsession.in
gdm-2.6.0.7/config/gdm.conf.in
gdm-2.6.0.7/config/default.desktop
gdm-2.6.0.7/config/CDE.desktop
gdm-2.6.0.7/config/gnome.desktop
gdm-2.6.0.7/config/default.desktop.in
gdm-2.6.0.7/config/gnome.desktop.in
gdm-2.6.0.7/config/CDE.desktop.in
gdm-2.6.0.7/config/gdm
gdm-2.6.0.7/config/gdm-autologin
gdm-2.6.0.7/config/locale.alias
gdm-2.6.0.7/config/PostLogin
gdm-2.6.0.7/config/XKeepsCrashing
gdm-2.6.0.7/config/gettextfoo.h
gdm-2.6.0.7/config/extract-shell.sh
gdm-2.6.0.7/daemon/Makefile.am
gdm-2.6.0.7/daemon/Makefile.in
gdm-2.6.0.7/daemon/gdm.in
gdm-2.6.0.7/daemon/gdm.c
gdm-2.6.0.7/daemon/gdm.h
gdm-2.6.0.7/daemon/display.c
gdm-2.6.0.7/daemon/display.h
gdm-2.6.0.7/daemon/slave.c
gdm-2.6.0.7/daemon/slave.h
gdm-2.6.0.7/daemon/server.c
gdm-2.6.0.7/daemon/server.h
gdm-2.6.0.7/daemon/misc.c
gdm-2.6.0.7/daemon/misc.h
gdm-2.6.0.7/daemon/auth.c
gdm-2.6.0.7/daemon/auth.h
gdm-2.6.0.7/daemon/cookie.c
gdm-2.6.0.7/daemon/cookie.h
gdm-2.6.0.7/daemon/xdmcp.c
gdm-2.6.0.7/daemon/xdmcp.h
gdm-2.6.0.7/daemon/choose.c
gdm-2.6.0.7/daemon/choose.h
gdm-2.6.0.7/daemon/filecheck.c
gdm-2.6.0.7/daemon/filecheck.h
gdm-2.6.0.7/daemon/md5.c
gdm-2.6.0.7/daemon/md5.h
gdm-2.6.0.7/daemon/verify-pam.c
gdm-2.6.0.7/daemon/getvt.c
gdm-2.6.0.7/daemon/verify.h
gdm-2.6.0.7/daemon/errorgui.c
gdm-2.6.0.7/daemon/errorgui.h
gdm-2.6.0.7/daemon/gdm-net.c
gdm-2.6.0.7/daemon/gdm-net.h
gdm-2.6.0.7/daemon/getvt.h
gdm-2.6.0.7/daemon/verify-crypt.c
gdm-2.6.0.7/daemon/verify-shadow.c
gdm-2.6.0.7/gui/modules/AccessDwellMouseEvents.in
gdm-2.6.0.7/gui/modules/AccessKeyMouseEvents.in
gdm-2.6.0.7/gui/modules/Makefile.am
gdm-2.6.0.7/gui/modules/Makefile.in
gdm-2.6.0.7/gui/modules/dwellmouselistener.c
gdm-2.6.0.7/gui/modules/keymouselistener.c
gdm-2.6.0.7/gui/Makefile.am
gdm-2.6.0.7/gui/Makefile.in
gdm-2.6.0.7/gui/gdmlanguages.c
gdm-2.6.0.7/gui/gdmlanguages.h
gdm-2.6.0.7/gui/misc.c
gdm-2.6.0.7/gui/misc.h
gdm-2.6.0.7/gui/gdmcommon.c
gdm-2.6.0.7/gui/gdmcommon.h
gdm-2.6.0.7/gui/gdmwm.c
gdm-2.6.0.7/gui/gdmwm.h
gdm-2.6.0.7/gui/gdmXnestchooser.c
gdm-2.6.0.7/gui/gdmcomm.c
gdm-2.6.0.7/gui/gdmcomm.h
gdm-2.6.0.7/gui/gdmchooser.c
gdm-2.6.0.7/gui/gdmflexiserver.c
gdm-2.6.0.7/gui/gdmlogin.c
gdm-2.6.0.7/gui/gdmphotosetup.c
gdm-2.6.0.7/gui/gdmsetup.c
gdm-2.6.0.7/gui/gdmsetup-strings.c
gdm-2.6.0.7/gui/gdmchooser-strings.c
gdm-2.6.0.7/gui/gdmsetup.gladep
gdm-2.6.0.7/gui/gdmchooser.gladep
gdm-2.6.0.7/gui/gdmsetup.glade
gdm-2.6.0.7/gui/gdmchooser.glade
gdm-2.6.0.7/gui/login-photo.png
gdm-2.6.0.7/gui/gdmsetup.desktop
gdm-2.6.0.7/gui/gdmflexiserver.desktop
gdm-2.6.0.7/gui/gdmflexiserver-xnest.desktop
gdm-2.6.0.7/gui/gdmsetup.desktop.in
gdm-2.6.0.7/gui/gdmflexiserver.desktop.in
gdm-2.6.0.7/gui/gdmflexiserver-xnest.desktop.in
gdm-2.6.0.7/gui/gdmphotosetup.desktop
gdm-2.6.0.7/gui/gdmphotosetup.desktop.in
gdm-2.6.0.7/gui/greeter/Makefile.am
gdm-2.6.0.7/gui/greeter/Makefile.in
gdm-2.6.0.7/gui/greeter/greeter.c
gdm-2.6.0.7/gui/greeter/greeter.h
gdm-2.6.0.7/gui/greeter/greeter_action_language.c
gdm-2.6.0.7/gui/greeter/greeter_action_language.h
gdm-2.6.0.7/gui/greeter/greeter_canvas_item.c
gdm-2.6.0.7/gui/greeter/greeter_canvas_item.h
gdm-2.6.0.7/gui/greeter/greeter_configuration.h
gdm-2.6.0.7/gui/greeter/greeter_events.c
gdm-2.6.0.7/gui/greeter/greeter_events.h
gdm-2.6.0.7/gui/greeter/greeter_geometry.c
gdm-2.6.0.7/gui/greeter/greeter_geometry.h
gdm-2.6.0.7/gui/greeter/greeter_item.c
gdm-2.6.0.7/gui/greeter/greeter_item_timed.c
gdm-2.6.0.7/gui/greeter/greeter_item_timed.h
gdm-2.6.0.7/gui/greeter/greeter_item_capslock.c
gdm-2.6.0.7/gui/greeter/greeter_item_capslock.h
gdm-2.6.0.7/gui/greeter/greeter_item_clock.c
gdm-2.6.0.7/gui/greeter/greeter_item_clock.h
gdm-2.6.0.7/gui/greeter/greeter_item.h
gdm-2.6.0.7/gui/greeter/greeter_item_pam.c
gdm-2.6.0.7/gui/greeter/greeter_item_pam.h
gdm-2.6.0.7/gui/greeter/greeter_item_ulist.c
gdm-2.6.0.7/gui/greeter/greeter_item_ulist.h
gdm-2.6.0.7/gui/greeter/greeter_item_customlist.c
gdm-2.6.0.7/gui/greeter/greeter_item_customlist.h
gdm-2.6.0.7/gui/greeter/greeter_parser.c
gdm-2.6.0.7/gui/greeter/greeter_parser.h
gdm-2.6.0.7/gui/greeter/greeter_session.c
gdm-2.6.0.7/gui/greeter/greeter_session.h
gdm-2.6.0.7/gui/greeter/greeter_system.c
gdm-2.6.0.7/gui/greeter/greeter_system.h
gdm-2.6.0.7/gui/greeter/gdmthemetester
gdm-2.6.0.7/gui/greeter/greeter.dtd
gdm-2.6.0.7/gui/greeter/themes/Makefile.am
gdm-2.6.0.7/gui/greeter/themes/Makefile.in
gdm-2.6.0.7/gui/greeter/themes/circles/Makefile.am
gdm-2.6.0.7/gui/greeter/themes/circles/Makefile.in
gdm-2.6.0.7/gui/greeter/themes/circles/GdmGreeterTheme.desktop
gdm-2.6.0.7/gui/greeter/themes/circles/circles.xml
gdm-2.6.0.7/gui/greeter/themes/circles/background.svg
gdm-2.6.0.7/gui/greeter/themes/circles/flower.png
gdm-2.6.0.7/gui/greeter/themes/circles/help.png
gdm-2.6.0.7/gui/greeter/themes/circles/options.png
gdm-2.6.0.7/gui/greeter/themes/circles/screenshot.png
gdm-2.6.0.7/gui/greeter/themes/circles/GdmGreeterTheme.desktop.in
gdm-2.6.0.7/gui/greeter/themes/happygnome/Makefile.am
gdm-2.6.0.7/gui/greeter/themes/happygnome/Makefile.in
gdm-2.6.0.7/gui/greeter/themes/happygnome/GdmGreeterTheme.desktop
gdm-2.6.0.7/gui/greeter/themes/happygnome/happygnome.xml
gdm-2.6.0.7/gui/greeter/themes/happygnome/background.svg
gdm-2.6.0.7/gui/greeter/themes/happygnome/disconnect.png
gdm-2.6.0.7/gui/greeter/themes/happygnome/gnome-logo.png
gdm-2.6.0.7/gui/greeter/themes/happygnome/options.png
gdm-2.6.0.7/gui/greeter/themes/happygnome/screenshot.png
gdm-2.6.0.7/gui/greeter/themes/happygnome/session.png
gdm-2.6.0.7/gui/greeter/themes/happygnome/system.png
gdm-2.6.0.7/gui/greeter/themes/happygnome/GdmGreeterTheme.desktop.in
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/Makefile.am
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/Makefile.in
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/GdmGreeterTheme.desktop
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/happygnome.xml
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/background.svg
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/disconnect.png
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/gnome-logo.png
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/options.png
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/screenshot.png
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/session.png
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/system.png
gdm-2.6.0.7/gui/greeter/themes/happygnome-list/GdmGreeterTheme.desktop.in
gdm-2.6.0.7/po/ChangeLog
gdm-2.6.0.7/po/Makefile.in.in
gdm-2.6.0.7/po/POTFILES.in
gdm-2.6.0.7/po/gdm.pot
gdm-2.6.0.7/po/af.po
gdm-2.6.0.7/po/am.po
gdm-2.6.0.7/po/ar.po
gdm-2.6.0.7/po/az.po
gdm-2.6.0.7/po/be.po
gdm-2.6.0.7/po/bg.po
gdm-2.6.0.7/po/bn.po
gdm-2.6.0.7/po/bs.po
gdm-2.6.0.7/po/ca.po
gdm-2.6.0.7/po/cs.po
gdm-2.6.0.7/po/cy.po
gdm-2.6.0.7/po/da.po
gdm-2.6.0.7/po/de.po
gdm-2.6.0.7/po/el.po
gdm-2.6.0.7/po/en_CA.po
gdm-2.6.0.7/po/en_GB.po
gdm-2.6.0.7/po/es.po
gdm-2.6.0.7/po/et.po
gdm-2.6.0.7/po/eu.po
gdm-2.6.0.7/po/fa.po
gdm-2.6.0.7/po/fi.po
gdm-2.6.0.7/po/fr.po
gdm-2.6.0.7/po/ga.po
gdm-2.6.0.7/po/gl.po
gdm-2.6.0.7/po/gu.po
gdm-2.6.0.7/po/he.po
gdm-2.6.0.7/po/hi.po
gdm-2.6.0.7/po/hr.po
gdm-2.6.0.7/po/hu.po
gdm-2.6.0.7/po/id.po
gdm-2.6.0.7/po/is.po
gdm-2.6.0.7/po/it.po
gdm-2.6.0.7/po/ja.po
gdm-2.6.0.7/po/ko.po
gdm-2.6.0.7/po/lt.po
gdm-2.6.0.7/po/lv.po
gdm-2.6.0.7/po/mi.po
gdm-2.6.0.7/po/mk.po
gdm-2.6.0.7/po/ml.po
gdm-2.6.0.7/po/mn.po
gdm-2.6.0.7/po/mr.po
gdm-2.6.0.7/po/ms.po
gdm-2.6.0.7/po/nb.po
gdm-2.6.0.7/po/nl.po
gdm-2.6.0.7/po/nn.po
gdm-2.6.0.7/po/no.po
gdm-2.6.0.7/po/nso.po
gdm-2.6.0.7/po/pa.po
gdm-2.6.0.7/po/pl.po
gdm-2.6.0.7/po/pt.po
gdm-2.6.0.7/po/pt_BR.po
gdm-2.6.0.7/po/ro.po
gdm-2.6.0.7/po/ru.po
gdm-2.6.0.7/po/sk.po
gdm-2.6.0.7/po/sl.po
gdm-2.6.0.7/po/sq.po
gdm-2.6.0.7/po/sr.po
gdm-2.6.0.7/po/sr@Latn.po
gdm-2.6.0.7/po/sv.po
gdm-2.6.0.7/po/ta.po
gdm-2.6.0.7/po/th.po
gdm-2.6.0.7/po/tr.po
gdm-2.6.0.7/po/uk.po
gdm-2.6.0.7/po/vi.po
gdm-2.6.0.7/po/wa.po
gdm-2.6.0.7/po/zh_CN.po
gdm-2.6.0.7/po/zh_TW.po
gdm-2.6.0.7/po/zu.po
gdm-2.6.0.7/po/af.gmo
gdm-2.6.0.7/po/am.gmo
gdm-2.6.0.7/po/ar.gmo
gdm-2.6.0.7/po/az.gmo
gdm-2.6.0.7/po/be.gmo
gdm-2.6.0.7/po/bg.gmo
gdm-2.6.0.7/po/bn.gmo
gdm-2.6.0.7/po/bs.gmo
gdm-2.6.0.7/po/ca.gmo
gdm-2.6.0.7/po/cs.gmo
gdm-2.6.0.7/po/cy.gmo
gdm-2.6.0.7/po/da.gmo
gdm-2.6.0.7/po/de.gmo
gdm-2.6.0.7/po/el.gmo
gdm-2.6.0.7/po/en_CA.gmo
gdm-2.6.0.7/po/en_GB.gmo
gdm-2.6.0.7/po/es.gmo
gdm-2.6.0.7/po/et.gmo
gdm-2.6.0.7/po/eu.gmo
gdm-2.6.0.7/po/fa.gmo
gdm-2.6.0.7/po/fi.gmo
gdm-2.6.0.7/po/fr.gmo
gdm-2.6.0.7/po/ga.gmo
gdm-2.6.0.7/po/gl.gmo
gdm-2.6.0.7/po/gu.gmo
gdm-2.6.0.7/po/he.gmo
gdm-2.6.0.7/po/hi.gmo
gdm-2.6.0.7/po/hr.gmo
gdm-2.6.0.7/po/hu.gmo
gdm-2.6.0.7/po/id.gmo
gdm-2.6.0.7/po/is.gmo
gdm-2.6.0.7/po/it.gmo
gdm-2.6.0.7/po/ja.gmo
gdm-2.6.0.7/po/ko.gmo
gdm-2.6.0.7/po/lt.gmo
gdm-2.6.0.7/po/lv.gmo
gdm-2.6.0.7/po/mi.gmo
gdm-2.6.0.7/po/mk.gmo
gdm-2.6.0.7/po/ml.gmo
gdm-2.6.0.7/po/mn.gmo
gdm-2.6.0.7/po/mr.gmo
gdm-2.6.0.7/po/ms.gmo
gdm-2.6.0.7/po/nb.gmo
gdm-2.6.0.7/po/nl.gmo
gdm-2.6.0.7/po/nn.gmo
gdm-2.6.0.7/po/no.gmo
gdm-2.6.0.7/po/nso.gmo
gdm-2.6.0.7/po/pa.gmo
gdm-2.6.0.7/po/pl.gmo
gdm-2.6.0.7/po/pt.gmo
gdm-2.6.0.7/po/pt_BR.gmo
gdm-2.6.0.7/po/ro.gmo
gdm-2.6.0.7/po/ru.gmo
gdm-2.6.0.7/po/sk.gmo
gdm-2.6.0.7/po/sl.gmo
gdm-2.6.0.7/po/sq.gmo
gdm-2.6.0.7/po/sr.gmo
gdm-2.6.0.7/po/sr@Latn.gmo
gdm-2.6.0.7/po/sv.gmo
gdm-2.6.0.7/po/ta.gmo
gdm-2.6.0.7/po/th.gmo
gdm-2.6.0.7/po/tr.gmo
gdm-2.6.0.7/po/uk.gmo
gdm-2.6.0.7/po/vi.gmo
gdm-2.6.0.7/po/wa.gmo
gdm-2.6.0.7/po/zh_CN.gmo
gdm-2.6.0.7/po/zh_TW.gmo
gdm-2.6.0.7/po/zu.gmo
gdm-2.6.0.7/README
gdm-2.6.0.7/configure.in
gdm-2.6.0.7/aclocal.m4
gdm-2.6.0.7/Makefile.am
gdm-2.6.0.7/Makefile.in
gdm-2.6.0.7/config.h.in
gdm-2.6.0.7/gdm-restart.in
gdm-2.6.0.7/gdm-safe-restart.in
gdm-2.6.0.7/gdm-stop.in
gdm-2.6.0.7/gdm.spec.in
gdm-2.6.0.7/gdmsetup-security.in
gdm-2.6.0.7/configure
gdm-2.6.0.7/AUTHORS
gdm-2.6.0.7/COPYING
gdm-2.6.0.7/ChangeLog
gdm-2.6.0.7/INSTALL
gdm-2.6.0.7/NEWS
gdm-2.6.0.7/TODO
gdm-2.6.0.7/acconfig.h
gdm-2.6.0.7/config.guess
gdm-2.6.0.7/config.sub
gdm-2.6.0.7/depcomp
gdm-2.6.0.7/install-sh
gdm-2.6.0.7/ltmain.sh
gdm-2.6.0.7/missing
gdm-2.6.0.7/mkinstalldirs
gdm-2.6.0.7/README.install
gdm-2.6.0.7/gdm.spec
gdm-2.6.0.7/gdmsetup-pam
gdm-2.6.0.7/intltool-extract.in
gdm-2.6.0.7/intltool-merge.in
gdm-2.6.0.7/intltool-update.in
gdm-2.6.0.7/gdmconfig
gdm-2.6.0.7/xmldocs.make
gdm-2.6.0.7/omf.make
gdm-2.6.0.7/pixmaps/Makefile.am
gdm-2.6.0.7/pixmaps/Makefile.in
gdm-2.6.0.7/pixmaps/gdm-foot-logo.png
gdm-2.6.0.7/pixmaps/nobody.png
gdm-2.6.0.7/pixmaps/nohost.png
gdm-2.6.0.7/pixmaps/16x16/Makefile.am
gdm-2.6.0.7/pixmaps/16x16/Makefile.in
gdm-2.6.0.7/pixmaps/16x16/gdm-xnest.png
gdm-2.6.0.7/pixmaps/32x32/Makefile.am
gdm-2.6.0.7/pixmaps/32x32/Makefile.in
gdm-2.6.0.7/pixmaps/32x32/gdm-setup.png
gdm-2.6.0.7/pixmaps/32x32/gdm-xnest.png
gdm-2.6.0.7/pixmaps/48x48/Makefile.am
gdm-2.6.0.7/pixmaps/48x48/Makefile.in
gdm-2.6.0.7/pixmaps/48x48/gdm.png
gdm-2.6.0.7/pixmaps/48x48/gdm-xnest.png
gdm-2.6.0.7/pixmaps/48x48/gdm-setup.png
gdm-2.6.0.7/vicious-extensions/README
gdm-2.6.0.7/vicious-extensions/Makefile.am
gdm-2.6.0.7/vicious-extensions/Makefile.in
gdm-2.6.0.7/vicious-extensions/COPYING.LIB
gdm-2.6.0.7/vicious-extensions/ChangeLog
gdm-2.6.0.7/vicious-extensions/ve-i18n.h
gdm-2.6.0.7/vicious-extensions/ve-misc.c
gdm-2.6.0.7/vicious-extensions/ve-misc.h
gdm-2.6.0.7/vicious-extensions/ve-config.c
gdm-2.6.0.7/vicious-extensions/ve-config.h
gdm-2.6.0.7/vicious-extensions/ve-signal.c
gdm-2.6.0.7/vicious-extensions/ve-signal.h
gdm-2.6.0.7/vicious-extensions/ve-gnome.c
gdm-2.6.0.7/vicious-extensions/vicious.h
gdm-2.6.0.7/vicious-extensions/ve-nongnome.c
gdm-2.6.0.7/vicious-extensions/glade-helper.c
gdm-2.6.0.7/vicious-extensions/glade-helper.h
gdm-2.6.0.7/vicious-extensions/ve-miscui.c
gdm-2.6.0.7/vicious-extensions/ve-miscui.h
gdm-2.6.0.7/vicious-extensions/viciousui.h
gdm-2.6.0.7/vicious-extensions/test-ve-config.c
gdm-2.6.0.7/utils/Makefile.am
gdm-2.6.0.7/utils/Makefile.in
gdm-2.6.0.7/utils/gdmaskpass.c
gdm-2.6.0.7/utils/gdmopen.c
gdm-2.6.0.7/utils/gdmtranslate.c
gdm-2.6.0.7/docs/Makefile.am
gdm-2.6.0.7/docs/Makefile.in
gdm-2.6.0.7/docs/gdm.1
gdm-2.6.0.7/docs/C/Makefile.am
gdm-2.6.0.7/docs/C/Makefile.in
gdm-2.6.0.7/docs/C/legal.xml
gdm-2.6.0.7/docs/C/gdm.xml
gdm-2.6.0.7/docs/C/gdm-C.omf
gdm-2.6.0.7/docs/de/Makefile.am
gdm-2.6.0.7/docs/de/Makefile.in
gdm-2.6.0.7/docs/de/legal.xml
gdm-2.6.0.7/docs/de/gdm.xml
gdm-2.6.0.7/docs/de/gdm-de.omf
gdm-2.6.0.7/docs/de/figures/gdm_window.png
gdm-2.6.0.7/docs/es/Makefile.am
gdm-2.6.0.7/docs/es/Makefile.in
gdm-2.6.0.7/docs/es/legal.xml
gdm-2.6.0.7/docs/es/gdm.xml
gdm-2.6.0.7/docs/es/gdm-es.omf
gdm-2.6.0.7/docs/es/figures/gdm_window.png
gdm-2.6.0.7/docs/fr/Makefile.am
gdm-2.6.0.7/docs/fr/Makefile.in
gdm-2.6.0.7/docs/fr/legal.xml
gdm-2.6.0.7/docs/fr/gdm.xml
gdm-2.6.0.7/docs/fr/gdm-fr.omf
gdm-2.6.0.7/docs/fr/figures/gdm_window.png
gdm-2.6.0.7/docs/it/Makefile.am
gdm-2.6.0.7/docs/it/Makefile.in
gdm-2.6.0.7/docs/it/legal.xml
gdm-2.6.0.7/docs/it/gdm.xml
gdm-2.6.0.7/docs/it/gdm-it.omf
gdm-2.6.0.7/docs/it/figures/gdm_window.png
gdm-2.6.0.7/docs/sv/Makefile.am
gdm-2.6.0.7/docs/sv/Makefile.in
gdm-2.6.0.7/docs/sv/legal.xml
gdm-2.6.0.7/docs/sv/gdm.xml
gdm-2.6.0.7/docs/sv/gdm-sv.omf
gdm-2.6.0.7/docs/sv/figures/gdm_window.png
gdm-2.6.0.7/docs/ja/Makefile.am
gdm-2.6.0.7/docs/ja/Makefile.in
gdm-2.6.0.7/docs/ja/legal.xml
gdm-2.6.0.7/docs/ja/gdm.xml
gdm-2.6.0.7/docs/ja/gdm-ja.omf
gdm-2.6.0.7/docs/ja/figures/gdm_window.png
gdm-2.6.0.7/docs/ko/Makefile.am
gdm-2.6.0.7/docs/ko/Makefile.in
gdm-2.6.0.7/docs/ko/legal.xml
gdm-2.6.0.7/docs/ko/gdm.xml
gdm-2.6.0.7/docs/ko/gdm-ko.omf
gdm-2.6.0.7/docs/ko/figures/gdm_window.png
gdm-2.6.0.7/docs/zh_CN/Makefile.am
gdm-2.6.0.7/docs/zh_CN/Makefile.in
gdm-2.6.0.7/docs/zh_CN/legal.xml
gdm-2.6.0.7/docs/zh_CN/gdm.xml
gdm-2.6.0.7/docs/zh_CN/gdm-zh_CN.omf
gdm-2.6.0.7/docs/zh_CN/figures/gdm_window.png
gdm-2.6.0.7/docs/zh_HK/Makefile.am
gdm-2.6.0.7/docs/zh_HK/Makefile.in
gdm-2.6.0.7/docs/zh_HK/legal.xml
gdm-2.6.0.7/docs/zh_HK/gdm.xml
gdm-2.6.0.7/docs/zh_HK/gdm-zh_HK.omf
gdm-2.6.0.7/docs/zh_HK/figures/gdm_window.png
gdm-2.6.0.7/docs/zh_TW/Makefile.am
gdm-2.6.0.7/docs/zh_TW/Makefile.in
gdm-2.6.0.7/docs/zh_TW/legal.xml
gdm-2.6.0.7/docs/zh_TW/gdm.xml
gdm-2.6.0.7/docs/zh_TW/gdm-zh_TW.omf
gdm-2.6.0.7/docs/zh_TW/figures/gdm_window.png
root@cafedescafeinat-OptiPlex-GX270:/home/cafedescafeinat/Escriptori# [B]ls
gdm-2.6.0.7  gdm-2.6.0.7.tar.bz2[/B]
root@cafedescafeinat-OptiPlex-GX270:/home/cafedescafeinat/Escriptori# **cd gdm-2.6.0.7**
root@cafedescafeinat-OptiPlex-GX270:/home/cafedescafeinat/Escriptori/gdm-2.6.0.7# **./configure**
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.28... 0.31.3 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for consolehelper... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
root@cafedescafeinat-OptiPlex-GX270:/home/cafedescafeinat/Escriptori/gdm-2.6.0.7# **make**
make: *** No targets specified and no makefile found.  Stop.
root@cafedescafeinat-OptiPlex-GX270:/home/cafedescafeinat/Escriptori/gdm-2.6.0.7# 



Suposo que l'error del C++ deu ser el motiu.. però m'ho podeu assegurar?

Ah, i faig servir el Ubuntu 10.10 català x86 :)

Us ho agraïré molt \\:D/

---

### Post by kimet on 2011-04-22
-Et falta algun paquet: cpp, instal.la també build-essential i c++ (no se si s'instal.len com a dependència de build essential)

-El ./compile i el make no cal que els executis com a root, només pel make install es necesari.

-Una altre vegada no enganxis aquestes parrafades tan llargues fes servir les etiquetes 'code' o un fitxer adjunt.

Salut.

---

### Post by cafedescafeinat on 2011-04-22
Ostres, 

Sento no haver fet res per evitar la parrafada. 

Tenia instal.lat tots els programes menys, al meu entendre el C++.. però ara em diu això a diferència del que em deia abans.

No voldria enviar-ho pas tot a fer punyetes, però té mala baba que el primer que toco per la terminal, no m'acabi de sortir bé :( i clar, tampoc entenc què setze jutges hi diu :S

Gràcies igualment eh

[HTML]configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking for X... no
checking for socklen_t... yes
checking for setresuid... yes
checking for setenv... yes
checking for unsetenv... yes
checking for clearenv... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.3.0 libglade-2.0 >= 1.99.2 libgnome-2.0 >= 1.96.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.3.0 libglade-2.0 >= 1.99.2 libgnome-2.0 >= 1.96.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
[/HTML]

---

### Post by wgarcia on 2011-04-23
Tres cosetes més:

1) Millor obrir un fil nou i no reaprofitar un fil vell per a un tema nou.

2) No fa falta fer el "configure" i "make" amb "sudo", i et complicarà la vida perquè això pot crear fitxers que després costin esborrar per haver estar creats com a superusuari.

3) Per ser el primer cop que vols compilar un paquet t'has ficat en un de força complicat, "gdm" és el gestor gràfic GNOME, òbviament ja compilat en tot sistema Ubuntu o similar que es basi en GNOME, i té com és obvi moltes dependències que s'ha de satisfer per poder-se compilar. Els missatges que aborten la compilació està relacionat amb això.

Potser doncs si obres un fil nou la podem continuar, i és interessant saber en primer lloc perquè necessites compilar aquest paquet.

---

