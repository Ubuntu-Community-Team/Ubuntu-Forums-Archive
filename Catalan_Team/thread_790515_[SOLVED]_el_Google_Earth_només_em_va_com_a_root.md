---
title: "[SOLVED] el Google Earth només em va com a root"
date: 2008-05-11
forum: Catalan Team
---

### Post by bikerbaixcamp on 2008-05-11
Ei, doncs ja us vaig comentat que el .bin del googleearth no s'obria, i la solució era executar el bin com a root. Així ho vaig fer i es va instal·lar a la carpeta "sergi". El que passa es que quan clico s'obre el Google Earth però no m'apareix la "bola del món" ni les opcions per editar ni res... 
Ara bé, quan entro a la carpeta com a sudo nautilus pel terminal (com a root vaja) i obro el GoogleEarth doncs es veu tot tal com toca i correcte.

També he provat de donar tots els permisos dels arxius de la carpeta del googleearth. Abans sortia a l'arxiu un petit candau i ara res. Però continua fent el mateix si és fa com usuari "normal".

Alguna solució?

Gràcies!

---

### Post by bikerbaixcamp on 2008-05-11
Ahh! I a més a més, abans he tornat a instalar el programar per a veure si la cosa anava. I he borrat la carpeta (ja que l'uninstall no funcionava) i ara a la paperera part d'aquest no em deixa moure-la ni borrar-la. I quan entro al nautilus com a sudo; doncs no em veu res a la carpeta.

:???:

---

### Post by papapep on 2008-05-11
> i la solució era executar el bin com a root

És que la solució no és aquesta. D'aquí et deriven els problemes que tens ara.
Per executar l'instal·lador del Google Earth només et cal que el fitxer .bin tingui permís d'execució i invocar-lo des d'un terminal:

```
~/Escriptori$ ./GoogleEarthLinux.bin
```

---

### Post by bikerbaixcamp on 2008-05-11
Fent això em surt: 

bash: /home/sergi/Escriptori$: No such file or directory

Però entenc que he de fer això en el meu cas, no?

/home/sergi/arxius/GoogleEarthLinux.bin

I si, em surt lo d'instal·lar. A partir d'aquí s'instal·la a la carpeta /home però passa el mateix d'abans. 

I la carpeta de la paperera tampoc es pot borrar.

---

### Post by papapep on 2008-05-11
Si des de dins la carpeta on has instal·lat el Google Earth fas:

```
./googleearth %f
```

què et surt?

---

### Post by bikerbaixcamp on 2008-05-11
Doncs el mateix. Sense la bona del món i amb les opcions desactivades. S'obre, però ja et dic fa això.

A la consola he posat això, era així no?

/home/sergi/googleearth/googleearth %f

---

### Post by papapep on 2008-05-11
Enganxa el que et mostrin les següents ordres:

```
ls -la /home/sergi | grep google*
```

```
ls -la /home/sergi/googleearth/
```

```
ls -la /home/sergi/google-earth/
```

---

### Post by bikerbaixcamp on 2008-05-11
> gi@sergi-desktop:~$ ls -la /home/sergi | grep google*
ls: no s’ha pogut accedir a /home/sergi/.gvfs: Transport endpoint is not connected
drwxr-xr-x 11 sergi sergi   4096 2008-05-11 20:19 googleearth
drwx------  5 sergi sergi   4096 2008-05-11 20:44 .googleearth
sergi@sergi-desktop:~$ ls -la /home/sergi/googleearth/
total 47536
drwxr-xr-x  11 sergi sergi    4096 2008-05-11 20:19 .
drwxr-xr-x  60 sergi sergi    4096 2008-05-11 21:36 ..
-rw-r--r--   1 sergi sergi   65030 2008-05-11 20:18 drivers.ini
drwxr-xr-x   2 sergi sergi    4096 2008-05-11 20:19 Google
-rwxrwxrwx   1 sergi sergi    1308 2008-05-11 20:18 googleearth
-rwxr-xr-x   1 sergi sergi   48148 2008-05-11 20:18 googleearth-bin
-rw-r--r--   1 sergi sergi    4787 2008-05-11 20:18 googleearth-icon.png
-rw-r--r--   1 sergi sergi     638 2008-05-11 20:18 googleearth-mimetypes.xml
-rw-r--r--   1 sergi sergi   17748 2008-05-11 20:18 googleearth.xpm
-rw-r--r--   1 sergi sergi     428 2008-05-11 20:18 Google-googleearth.desktop
-rw-r--r--   1 sergi sergi   18011 2008-05-11 20:18 gpl.txt
-rwxr-xr-x   1 sergi sergi  258108 2008-05-11 20:18 gpsbabel
-rw-r--r--   1 sergi sergi     983 2008-05-11 20:18 ImporterGlobalSettings.ini
-rw-r--r--   1 sergi sergi    5054 2008-05-11 20:18 ImporterUISettings.ini
-rw-r--r--   1 sergi sergi       0 2008-05-11 20:18 kh20
drwxr-xr-x   2 sergi sergi    4096 2008-05-11 20:18 kvw
drwxr-xr-x   2 sergi sergi    4096 2008-05-11 20:18 lang
-rwxr-xr-x   1 sergi sergi   13376 2008-05-11 20:18 libalchemyext.so
-rwxr-xr-x   1 sergi sergi   11192 2008-05-11 20:18 libapiloader.so
-rwxr-xr-x   1 sergi sergi  335416 2008-05-11 20:18 libauth.so
-rwxr-xr-x   1 sergi sergi  557896 2008-05-11 20:18 libbase.so
-rwxr-xr-x   1 sergi sergi    4164 2008-05-11 20:18 libbasicingest.so
-rwxr-xr-x   1 sergi sergi 3122472 2008-05-11 20:18 libcollada-1.4.so
-rwxr-xr-x   1 sergi sergi  264196 2008-05-11 20:18 libcollada.so
-rwxr-xr-x   1 sergi sergi  806184 2008-05-11 20:18 libcommon.so
-rwxr-xr-x   1 sergi sergi   21604 2008-05-11 20:18 libcomponentframework.so
-rwxr-xr-x   1 sergi sergi 1196036 2008-05-11 20:18 libcrypto.so.0.9.8
-rwxr-xr-x   1 sergi sergi  209928 2008-05-11 20:18 libcurl.so.4
-rwxr-xr-x   1 sergi sergi 5316840 2008-05-11 20:18 libevll.so
-rwxr-xr-x   1 sergi sergi  811776 2008-05-11 20:18 libflightsim.so
-rwxr-xr-x   1 sergi sergi  794812 2008-05-11 20:18 libfreeimage.so.3
-rwxr-xr-x   1 sergi sergi   13348 2008-05-11 20:18 libfusioncommon.so
-rw-r--r--   1 sergi sergi   42272 2008-05-11 20:18 libgcc_s.so.1
-rwxr-xr-x   1 sergi sergi 3235956 2008-05-11 20:18 libgdal.so
-rwxr-xr-x   1 sergi sergi  210664 2008-05-11 20:18 libge_net.so
-rwxr-xr-x   1 sergi sergi 3354716 2008-05-11 20:18 libgeobase.so
-rwxr-xr-x   1 sergi sergi  517084 2008-05-11 20:18 libGLU.so.1
-rwxr-xr-x   1 sergi sergi  987444 2008-05-11 20:18 libgoogleearth_lib.so
-rwxr-xr-x   1 sergi sergi  450816 2008-05-11 20:18 libgooglesearch.so
-rwxr-xr-x   1 sergi sergi  516488 2008-05-11 20:18 libgps.so
-rwxr-xr-x   1 sergi sergi  415112 2008-05-11 20:18 libicudata.so.38
-rwxr-xr-x   1 sergi sergi 1087360 2008-05-11 20:18 libicuuc.so.38
-rwxr-xr-x   1 sergi sergi  399636 2008-05-11 20:18 libIGAttrs.so
-rwxr-xr-x   1 sergi sergi   62512 2008-05-11 20:18 libIGCollision.so
-rwxr-xr-x   1 sergi sergi  977852 2008-05-11 20:18 libIGCore.so
-rwxr-xr-x   1 sergi sergi   78392 2008-05-11 20:18 libIGDisplay.so
-rwxr-xr-x   1 sergi sergi  546512 2008-05-11 20:18 libIGExportCommon.so
-rwxr-xr-x   1 sergi sergi  746016 2008-05-11 20:18 libIGGfx.so
-rwxr-xr-x   1 sergi sergi  257464 2008-05-11 20:18 libIGGui.so
-rwxr-xr-x   1 sergi sergi  289872 2008-05-11 20:18 libIGMath.so
-rwxr-xr-x   1 sergi sergi  871292 2008-05-11 20:18 libIGOpt.so
-rwxr-xr-x   1 sergi sergi 1094236 2008-05-11 20:18 libIGSg.so
-rwxr-xr-x   1 sergi sergi  156408 2008-05-11 20:18 libIGUtils.so
-rwxr-xr-x   1 sergi sergi  140076 2008-05-11 20:18 libinput_plugin.so
-rwxr-xr-x   1 sergi sergi  143028 2008-05-11 20:18 libjpeg.so.62
-rwxr-xr-x   1 sergi sergi 1598960 2008-05-11 20:18 liblayer.so
-rwxr-xr-x   1 sergi sergi  135164 2008-05-11 20:18 libmath.so
-rwxr-xr-x   1 sergi sergi  400632 2008-05-11 20:18 libmeasure.so
-rwxr-xr-x   1 sergi sergi   23532 2008-05-11 20:18 libminizip.so
-rwxr-xr-x   1 sergi sergi  380796 2008-05-11 20:18 libmng.so.1
-rwxr-xr-x   1 sergi sergi   39636 2008-05-11 20:18 libmoduleframework.so
-rwxr-xr-x   1 sergi sergi 1112968 2008-05-11 20:18 libnavigate.so
-rwxr-xr-x   1 sergi sergi  160032 2008-05-11 20:18 libpng12.so.0
-rwxr-xr-x   1 sergi sergi   14340 2008-05-11 20:18 libport.so
-rwxr-xr-x   1 sergi sergi  208088 2008-05-11 20:18 libproj.so.0
-rwxr-xr-x   1 sergi sergi 2323988 2008-05-11 20:18 libQt3Support.so.4
-rwxr-xr-x   1 sergi sergi 1823904 2008-05-11 20:18 libQtCore.so.4
-rwxr-xr-x   1 sergi sergi 6486672 2008-05-11 20:18 libQtGui.so.4
-rwxr-xr-x   1 sergi sergi  541908 2008-05-11 20:18 libQtNetwork.so.4
-rwxr-xr-x   1 sergi sergi  165176 2008-05-11 20:18 libQtSql.so.4
-rwxr-xr-x   1 sergi sergi  322248 2008-05-11 20:18 libQtXml.so.4
-rwxr-xr-x   1 sergi sergi  242008 2008-05-11 20:18 librender.so
-rwxr-xr-x   1 sergi sergi  871596 2008-05-11 20:18 libstdc++.so.6
-rwxr-xr-x   1 sergi sergi  374644 2008-05-11 20:18 libtiff.so.3
-rwxr-xr-x   1 sergi sergi  401640 2008-05-11 20:18 libwmsbase.so
-rwxr-xr-x   1 sergi sergi   89476 2008-05-11 20:18 libz.so.1
drwxr-xr-x   3 sergi sergi    4096 2008-05-11 20:18 linux
drwxr-xr-x   3 sergi sergi    4096 2008-05-11 20:18 .manifest
-rw-r--r--   1 sergi sergi     661 2008-05-11 20:18 PCOptimizations.ini
drwxr-xr-x   3 sergi sergi    4096 2008-05-11 20:18 plugins
-rw-r--r--   1 sergi sergi       7 2008-05-11 20:18 qt.conf
drwxr-xr-x 267 sergi sergi   24576 2008-05-11 20:18 resources
drwxr-xr-x   2 sergi sergi    4096 2008-05-11 20:18 shaders
-rwxr-xr-x   1 sergi sergi    1708 2008-05-11 20:18 uninstall
drwxr-xr-x   2 sergi sergi    4096 2008-05-11 20:18 xml
sergi@sergi-desktop:~$ ls -la /home/sergi/google-earth/
ls: no s’ha pogut accedir a /home/sergi/google-earth/: No such file or directory
sergi@sergi-desktop:~$ 


I continua igual el Google Earth

;)

---

### Post by papapep on 2008-05-11
No sé noi, tot sembla que estigui bé. Només he vist una cosa que m'ha cridat l'atenció:

> ls: no s’ha pogut accedir a /home/sergi/.gvfs: Transport endpoint is not connected

Podria ser que fos la causa del teu problema, però és curiós que només se't manifesti amb el programa aquest...:
[https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/212789](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/212789)

---

### Post by bikerbaixcamp on 2008-05-11
Vaja que estic de pega. De totes maneres gràcies.

Ara he pensat una manera "cutre", però a veure si funciona.

Primer de tot com borrar lo de la paperera, que és un tros de la carpeta del google-earth abans instal·lat i que le tret amb el supr.

I d'altra banda, com desinstal·ar per complet el Google Earth, de manera que quedi ben borrat.

Després el tornaré a instal·lar amb els passos correctes i a veure...

Moltes gràcies!

---

### Post by jmaspons on 2008-05-14
Si et vols estalviar problemes pots mirar d'instal·lar google Earth des dels repositoris de [medibuntu.org]("http://medibuntu.org").

A mi em va finíssim.

Salut!

---

### Post by lluisanunez on 2008-05-14
> **bikerbaixcamp said:**
> 
Primer de tot com borrar lo de la paperera, que és un tros de la carpeta del google-earth abans instal·lat i que le tret amb el supr.


Fes
```
gksudo nautilus
```Ves a /home/sergi/ i fes CTRL-H per mostrar els arxius ocults
I veuràs la paperera que és ./Trash

Els fitxers de Googleearth els trobaràs tots a les carpetes /home/sergi/google-earth i /home/sergi/.googleearth, si els esborres quedarà desinsta&#320;lat
També a /home/sergi/google-earth trobaràs un script "uninstall" per desinsta&#320;lar-lo, l'hauràs d'executar amb sudo

---

### Post by bratac on 2008-05-16
Bones, com puc executar l'script que es diu uninstall ?

gràcies

---

### Post by lluisanunez on 2008-05-16
```
cd google-earth
chmod 555 uninstall
./uninstall
```

---

### Post by Diegstroyer on 2008-05-18
Has d'anar a la carpeta .config del teu home i canviar el permisos/propietari de l'arxiu Google, que els te el root, per el teu usuari (fes-ho amb chmod).

Apa, ja està:guitar:.

---

### Post by bikerbaixcamp on 2008-05-18
> **Diegstroyer said:**
> Has d'anar a la carpeta .config del teu home i canviar el permisos/propietari de l'arxiu Google, que els te el root, per el teu usuari (fes-ho amb chmod).

Apa, ja està:guitar:.

Oh, gràcies!!! :-P Això m'ha funcionat, per fi! ;-)

Ara només falta la carpeta que està a la paperera i no marxa. Vaig entrar a /home/sergi però ni a fitxers ocults hi havia la carpeta trash. A veure si es pot esborrar..

Vinga, salutacions ubunteres!

---

### Post by bratac on 2008-05-18
Bones, 

quan faig l'chmod, em diu el següent:

> bratac@portatil:/opt/google-earth$ sudo chmod 555 uninstall
[sudo] password for bratac: 
bratac@portatil:/opt/google-earth$ ./uninstall
Could not find a usable uninstall program. Aborting.
bratac@portatil:/opt/google-earth$ 


Sóc a la carpeta del google earth i no em deixa, em podeu ajudar?

gràcies

---

### Post by lluisanunez on 2008-05-18
Suposo que has d'executar l'uninstall també com a root, o sigui prefixant amb sudo
Per cert, si estàs amb Hardy, m'he enterat que la paperera s'ha mogut a ~/.local/share/Trash

---

### Post by bratac on 2008-05-18
Em continua donant el mateix error :(

> bratac@portatil:/opt/google-earth$ sudo chmod 555 uninstall
[sudo] password for bratac: 
bratac@portatil:/opt/google-earth$ sudo ./uninstall
Could not find a usable uninstall program. Aborting.


Alguna altra idea?

gràcies

---

### Post by bikerbaixcamp on 2008-05-19
Ei si, solucionat. Es veu que ha canviat de lloc.

Admins, quan aquest noi hagi acabat de solucionar el seu dubte ja es pot fer un [solved].

Gràcies a tots!

---

### Post by bratac on 2008-05-22
Ja l'he desinstal·lat. Ho he fet de la següent manera:

> sudo su -
cd /opt/google-earth/
export DISPLAY=:0
./uninstall


Gràcies per la vostra ajuda!

Ja podeu posar un solved!

---

### Post by papapep on 2008-05-22
> Ja podeu posar un solved!

Posa'l tu mateix, si us plau.

EDITO: Ara veig que no l'has iniciat tu. En tot cas l'ha de donar per resolt el que l'ha creat.

---

