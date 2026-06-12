---
title: "Vídeos a l'ipod"
date: 2008-04-09
forum: Catalan Team
---

### Post by Joan Marc on 2008-04-09
Hola,
He estat buscant, però no he trobat massa cosa. 
Vull passar uns vídeos que m'he baixat del YouTube, al meu iPod.
Els vídeos són en format .flv, i l'iPod nomès accepta els formats .mp4.
Sabeu d'algun programa que em permeti transformar aquests dos formats, i un altre programa que em permeti passar-los a l'iPod?
Resulta que per passar la música hi ha uns quants programes que ho fan, però per passar els vídeos, no n'he trobat cap.

Gràcies

PD: M'he mirat aquest altre [fil]("http://ubuntuforums.org/showthread.php?t=558619&highlight=psp"), que perla dels vídeos per a la PSP (que comparteixen format), però el programa pspvc m'ha semblat que era per a windows.

---

### Post by patrickfromspain on 2008-04-09
el pspvc es per a linux i funciona be amb ubuntu, encara que el vaig haver de compilar.

També esta el thin liquid film [http://thinliquidfilm.org/](http://thinliquidfilm.org/)

salut

---

### Post by CarlesOriol on 2008-04-09
Fes un script

```
mencoder -ovc copy -oac mp3lame -lameopts mode=1:cbr:br=64 "$1" -o "$1.temp.avi" 

mencoder -ovc lavc -lavcopts vpass=1:vcodec=mpeg4:threads=2:vbitrate=256 -oac copy "$1.temp.avi" -o /dev/null

mencoder -ovc lavc -lavcopts vpass=2:vcodec=mpeg4:threads=2:vbitrate=256 -oac copy "$1.temp.avi" -o "$1.avi" 

rm "$1.temp.avi" 
rm ./divx2pass.log
```

---------------------------------------------

Edito: perdona. No t'havia comentat que et deixava l'script com a referència per convertir a mp4. Els requeriments de mida / bitrate, etc del ipod no els conec. Però segur que no ha de canviar massa.

---

### Post by Joan Marc on 2008-04-09
Perdona'm Carles, però la meva ignorància no em permet entendre què he de fer. Ho he de posar al terminal, guardaro en un arxiu de text...¿??¿?

---

### Post by Joan Marc on 2008-04-09
patrickfromspain: a l'intentar instal·lar el thin liquid film em surt el següent:
```
gami@gami:~$ sudo /home/gami/Escriptori/thinliquidfilm/install.py
[sudo] password for gami:
*************************************
      installing thinliquidfilm
*************************************


-------------------------
Checking dependencies ...
-------------------------

Couldn't find pyqt.  thin liquid film will not work without pyqt.  Aborting installation.
gami@gami:~$ 
```

Em diu ue no troba pyqt... què és?

---

### Post by pespin on 2008-04-09
Et falten les llibreries gràfiques Qt (les que utilitza el KDE) per a python.

Prova amb:

sudo aptitude install python2.5-qt4

---

### Post by Joan Marc on 2008-04-09
pespin: He instal·lat les llibreries que em deies, però continua sense trobar el pyqt

Gràcies de totes maneres

---

### Post by patrickfromspain on 2008-04-10
has d'instalar les llibreries de desenvolupament:

sudo apt-get install python-qt-dev

---

### Post by Joan Marc on 2008-04-12
També he instal·lat les que em dius patrickfromspain, però tampoc funciona :(

---

### Post by CarlesOriol on 2008-04-12
Una altra opció:

ffmpeg -i videooriginal.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 16:9 videoipod.mov

Escriu això en el terminal i canvia el videooriginal.avi i videoipod.mov per el nom de l'arxiu a convertir i el nom de l'arxiu en ormat ipod.

Cal que tinguis insta&#320;lat el ffmpeg :-)

---

### Post by Joan Marc on 2008-04-12
CarlesOriol: El format del video original és .flv, i quan ho poso tot al terminal, no l'accepta.

Gracies.

---

### Post by CarlesOriol on 2008-04-12
Llavors usa l'script que t'he indicat abans  (crea un document de text amb el gedit i després cal donar-li permisos d'execució)... però cerca informació al mencoder per tal de fer el canvi de mida del video a 320x240.

---

