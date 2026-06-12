---
title: "[SOLVED] Preparant la hardy"
date: 2008-04-04
forum: Catalan Team
---

### Post by xoldy on 2008-04-04
Hola a tots, voldria saber si hi ha manera de fer clonació del sistema a dia d'avui, per si hi ha un daltabaix actualitzant a Hardy. Tinc un disc extern usb. podria fer la clonació en aquest disc? com la recupero després?

Moltes gràcies

---

### Post by jodufi on 2008-04-04
Com es recomana en altres fils, pots utilitzar l'Unison

[http://ubuntuforums.org/showthread.php?t=741809](http://ubuntuforums.org/showthread.php?t=741809)
[http://ubuntuforums.org/showthread.php?t=470801](http://ubuntuforums.org/showthread.php?t=470801)

O directament copies tots els fitxers de la carpeta de l'usuari :)

---

### Post by xoldy on 2008-04-04
Ostres gràcies, perdó, evidentment he desobeït la norma de buscar primer al fòrum....

---

### Post by jodufi on 2008-04-04
Fet memòria he recordat un programa que et pot servir i promet bastant:

[http://www.conduit-project.org/](http://www.conduit-project.org/)

---

### Post by papapep on 2008-04-04
Compte, que no és exactament el que en Xoldy demanava. El Conduit aquest té molt bona pinta, però sembla que només tracta dades personals, no copia altres parts del sistema de fitxers.

---

### Post by jodufi on 2008-04-05
Discrepo papapep, segons la pàgina web del conduit:

*Conduit is a synchronization application for GNOME. It allows you to synchronize your files, photos, emails, contacts, notes, calendar data and any other type of personal information and synchronize that data with another computer, an online service, or even another electronic device.*

I mirant les captures, apareix una opció on posa «Files» i una altra «Folder».
[http://www.conduit-project.org/wiki/Screenshots](http://www.conduit-project.org/wiki/Screenshots)

Per tant hauria de poder sincronitzar fitxers i companyia.

Tot i això, s'hauria de provar per a confirmar-ho.

---

### Post by xoldy on 2008-04-05
Moltes gràcies, em posaré a fer proves i ja us diré que tal.

---

### Post by CarlesOriol on 2008-04-05
Jodufi:

He provat pel teu post el conduit. Té una pinta impresionant però se m'ha penjat sempre a mitja copia.
Crec que en poc temps serà un dels bons programes de referència del gnome però jo ara per ara no l'usaria per fer copies de seguretat.

L'unison sembla que està força bé ... però per un cop anem jo i en papapep creuats.

Per mi no hi ha com preparar un script en el terminal que faci 

```
rsync -urvt carpetaorigen carpetadestí
```

---

### Post by xoldy on 2008-04-05
Pregunto, a l'ubuntu hi ha la possibilitat de dir mira, tinc el sistema funcionant amb les aplicacions que faig servir, i vull fer un "ghost" (ja se que és windows, però és molt gràfic) a dia d'avui, per si el vull recuperar després de fer el cafre amb la instal·lació. L'unison no em servirà oi?, pel que he entés fa un mirror oi?

Merci com sempre

---

### Post by papapep on 2008-04-05
> però per un cop anem jo i en papapep creuats.

I després em diuen integrista del terminal :-D

Unison és una interfície gràfica de rsync que fa molts (ben bé cinc) anys que toco, i per això me'n refio, no us penseu que ja defalleixo :-P

Respecte el tema de fer una imatge del sistema que tens funcionant, si és a disc pots fer-ho amb dd o similar, que fa una còpia bit a bit (de fet estic segur que això ja s'ha parlat al fòrum). També hi ha el [systemimager]("http://wiki.systemimager.org/index.php/Main_Page"), [MkCdRec]("http://mkcdrec.ota.be/"), [Mondo Rescue]("http://www.mondorescue.org/"), etc.

---

### Post by patrickfromspain on 2008-04-05
ja ja.. l'edat et pot eh?

---

### Post by pespin on 2008-04-05
> que fa una còpia bit a bit

Hi ha alguna diferència entre la copia bit a bit i la copia de la ordre cp o similars?

---

### Post by CarlesOriol on 2008-04-06
**xoldy:**

Per copiar el suport (disc o partició) jo uso el partimage. Pots engegar amb una live, afegeixes el repositori universe i l'insta&#320;les. 

El partimage funciona com el ghost i fins i tot hi ha la possibilitat de fer copies sobre xarxa.

Hi ha cds vius que ja el porten de sortida com el systemrescue. Molt utils de dur sempre a la bossa, o fins i tot en ordinadors d'amics pots muntar una minipartició amb un xubuntu o en mode text (tipus server) on installar les eines de recuperació i guardar una copia del sistema just insta&#320;lat. (jo ho faig.. així quan es carreguen el sistema els el recuperes en un moment)

**pepsin, papapep:**

Totes les copies son bit a bit, en el que demana el joldy la copia es fa del suport.
Et poso un exemple si el disc dur fos un llibre

Amb el cp copiariem sempre l'original, l'escriuriem tot de nou en fulls blancs.

Amb el rsync ( o unison) copiariem l'original, l'escriuriem tot de nou en fulls blancs. Però les copies succesives canviariem sols els fulls on hi han canvis i eliminariem aquest que han estat eliminats de l'original.

Amb una eina tipus partimage o similar fariem una fotocopia (una fotocopia exactament igual que l'original) de tot el llibre.

----------------------------------------------

I jo que uso?

Per copiar la carpeta home ... un rsync així la tinc sincronitzada amb un servidor de copies i un disc dur extern usb (mai se sap :-) )

Quan canvio una màquina però vull conservar-ne el contingut, vull canviar un disc dur: partimage (aquest procés a més té un avantatge brutal respecte al windows. En windows pots fer una imatge d'un ordinador i dur-lo a un altre... però la llicència es perd pel camí ja que és una màquina diferent)

... i desde fa poc i gràcies a en RainCT encara tinc una eina més apassionant. El bazar. (bzr) Aquesta eina serveix per en la mateixa carpeta de treball, anar guardant fotos de tots els canvis que es van fent tant si treballes sol com en grup. I així pots restaurar la situació de qualsevolmoment anterior.
Un cop "versionada" o fotografiada la versió actual aquesta pot ser sincronitzada en un servidor remot actualitzant sols les diferències. (us adjunto una copia de seguiment del bzr al freevial per que us feu una idea).[ATTACH]65083[/ATTACH]

---

### Post by patrickfromspain on 2008-04-06
carles, jo tinc un disc extern usb. Si faig un rsync /home/patrick /media/disc-dur, hem fara una copia de tot el que hi ha a /home/patrick, correcte? Suposo que si despres d'un mes faig un altre rsync, es refa la copia, actualitzant el que calgui, borrant el fitxers que ja no hi son y copiant els nous. Es aixi?

Despres, per recuperar, es tan senzill com fer rsync a la inversa?

gracies!

---

### Post by papapep on 2008-04-06
Per mantenir les dades de dos llocs (directoris, discs, etc)  diferents sincronizades, definitivament rsync, sigui amb Unison o a pèl. 
Per clonar o fer imatges de discs o particions, partimage o dd, depenent de les característiques i la mida.

---

### Post by xoldy on 2008-04-06
Gràcies Carles, és això el que buscava, en el primer missatge no havia concretat massa. Ja l'he instal·lat i em poso mans a l'obra. Imagino que fent l'actualització a Hardy no tindré cap problema, però millor prevenir-se...
El bazar deu ser molt útil en entorns de xarxa, per poder fer "fotos" de les màquines crítiques.

S'aprén un munt amb vosaltres!

---

### Post by papapep on 2008-04-06
> Hi ha alguna diferència entre la copia bit a bit i la copia de la ordre cp o similars?

Una còpia bit a bit copia literalment el contingut d'un dispositiu físic, fins i tot els espais on no hi ha dades (tot i que hi ha una versió evolucionada de dd que esquiva els espais en blanc), fent una rèplica exacte del dispositiu original.
El cp només copia les dades existents, sense importar-li que el resultat sigui físicament idèntic o no.

---

### Post by CarlesOriol on 2008-04-06
patrickfromspain:

rsync

  -u = Actualitza la carpet destí sols amb els arxius nous o canviats
 --delete elimina a destí els arxius que ja no son a l'original

i si

recuperar la copia és el mateix que fer-la.

Per cert part (retallada) del meu script de l'udev per quan connecto el meu disc dur extern USB:

```

#1. Comprovar que el dispositiu existeix i la carpeta de copies

if [ -d /media/copiadisc/copies/carles ]
then

#    2 fer la copia
	rsync -urvt --delete --delete-excluded --exclude="carles/.googleearth/*" --exclude "carles/descarregues/*" --exclude="carles/.thumbnails/*" --exclude="carles/.Trash/*"  --exclude="carles/.cache/*" --exclude="carles/.beagle/*" /home/carles /media/copiadisc/copies

fi
```

---

### Post by CarlesOriol on 2008-04-06
> **xoldy said:**
> El bazar deu ser molt útil en entorns de xarxa, per poder fer "fotos" de les màquines crítiques.

No. Per fer fotos de màquines el partimage.

Per fer fotos de l'estat d'una carpeta i treballar en grup: el bazar (bzr)

---

### Post by CarlesOriol on 2008-04-06
Per cert... seguint amb aquest apasionan fil solved.

Fa temps vaig llegir que una de les novetats de la hardy és la insta&#320;lació en un ordinador amb un linux anterior amb una carpeta /home/usuari on esborra tot el disc excepte les carpetes d'usuari.

Algú ho ha provat?

---

### Post by patrickfromspain on 2008-04-06
mm una pregunta... el disc de desti no hauria de ser ntfs no? De fet, pot ser-ho?

EDITO: si no pot ser-ho, en que ho formatejo? ext2 o ext3, valtres com el teniu organitzat el disc dur?

salut!

---

### Post by CarlesOriol on 2008-04-06
Si el destí és ntfs perdras els permisos i els enllaços.

El meu disc dur extern està en ext3, i l'ordinador de xarxa en ntfs (per poc temps ja).

Una opció que havia provat fa temps, era crear un arxiu buit gran en el ntfs i dins inserir un sistema ext3 que muntava al fer la copia. ( munto ntfs i dins un arxiu amb un ext3 )

---

### Post by patrickfromspain on 2008-04-06
> **CarlesOriol said:**
> patrickfromspain:

rsync

  -u = Actualitza la carpet destí sols amb els arxius nous o canviats
 --delete elimina a destí els arxius que ja no son a l'original

i si

recuperar la copia és el mateix que fer-la.

Per cert part (retallada) del meu script de l'udev per quan connecto el meu disc dur extern USB:

```

#1. Comprovar que el dispositiu existeix i la carpeta de copies

if [ -d /media/copiadisc/copies/carles ]
then

#    2 fer la copia
	rsync -urvt --delete --delete-excluded --exclude="carles/.googleearth/*" --exclude "carles/descarregues/*" --exclude="carles/.thumbnails/*" --exclude="carles/.Trash/*"  --exclude="carles/.cache/*" --exclude="carles/.beagle/*" /home/carles /media/copiadisc/copies

fi
```
Aixo té bona pinta, i vull intentar fer alguna cosa similiar i de fet ja se com posar una regla udev que només afecti al meu dispositiu i com fer que s'executi aquesta ordre quan connecti el disc dur. 

Però tinc un dubte referent a.. que pasa si dema fas, per error, un sudo rm -rf /home/carles/* en comptes de /home/carles/carpeta/*? Si, clar, l'error es una mica bestia, pero pot pasar, no? Si passa aixo i connectes el teu disc dur sense eliminar o desactiva la regla.. et carrergues la copia de seguretat no?

Ja, ja... es de ser molt bestia si a sobre de cargarte el teu home enxufes el disc dur sense desactivar la regla.. pero nomes es per veure si ho he pillat tot be.

EDITO: si faig que es faci un rsync de /media/dades/mp3 i aquesta carpeta no existeix, cap problema, no?

salut!

---

### Post by papapep on 2008-04-06
Sense arribar a aquest cas tan bèstia que tu exposes, només amb que esborris sense voler un fitxer valuós del "master", el pots perdre dels dos dispositius quan sincronitzis, i pots causar un daltabaix. Per això jo mai li dic a l'rsync que esborri de la "còpia" el que ja no sigui al "màster", per que el considero més una còpia de seguretat històrica que no pas per fer un mirall del "master".
Aquest sistema porta més feina de fer neteja de tant en quant a la còpia, però em deixa dormir més tranquil...(però, evidentment, tot va per gustos).

> si faig que es faci un rsync de /media/dades/mp3 i aquesta carpeta no existeix, cap problema, no?

Si és l'origen no.

---

### Post by CarlesOriol on 2008-04-06
> **patrickfromspain said:**
> Però tinc un dubte referent a.. que pasa si dema fas, per error, un sudo rm -rf /home/carles/* en comptes de /home/carles/carpeta/*? Si, clar, l'error es una mica bestia, pero pot pasar, no? Si passa aixo i connectes el teu disc dur sense eliminar o desactiva la regla.. et carrergues la copia de seguretat no?

He he !!! bona pregunta :-D El raonament és correcte però hi ha un problema... l'script està a la meva carpeta d'usuari. Per tant no funcionaria.

---

### Post by patrickfromspain on 2008-04-06
que cabron.. bona aquesta :)

Una altra questió. De moment, estic experimentant amb això de l'udev de manera que li faig executar /etc/udev/copia.sh quan connecto el disc. El problema, es que sembla que el disc es monta despres d'executar la comanda.

Ho faig aixi: 

arxiu /etc/udev/rules.d/10-copia-seguretat.rules
BUS=="usb", ATTRS{manufacturer}=="Western Digital ", ATTRS{product}=="External HDD    ", ATTRS{serial}=="575845583036383637343036", NAME="WD120", RUN+="/etc/udev/copia.sh"

arxiu /etc/udev/copia.sh
if [ -d /media/WD120 ] 
then
	/usr/bin/rsync -ur --exclude=/home/patrick/VirtualBox --exclude=/home/patrick/.thumbnails --exclude=/home/patrick/.Trash --exclude=/home/patrick/.cache --exclude=/home/patrick/Examples --exclude=/home/patrick/Escriptori /home/patrick /media/WD120/copia-home
	/usr/bin/rsync -ur /media/dades/mp3 /media/WD120

else /usr/bin/touch /home/patrick/sense-fitxer
fi

tu com ho tens muntat?

Gracies!

---

### Post by CarlesOriol on 2008-04-07
KERNEL=="sd[a-z]1", SYSFS{model}=="MP0402H         ", ACTION=="add", RUN+="/home/carles/scripts/copiahdd.sh"

i 

a l'script com que soc desconfiat de que s'executi: 

**sleep 30**
echo Copia a Hdd USB TEST - $(date) >> /home/carles/scripts/logs/copies.log 

a inici i final

---

### Post by patrickfromspain on 2008-04-07
no hi ha manera!!! He probat de tot, i sempre passa el mateix: primer executa l'script i despres monta el disc, per tant l'script no serveix de res.

Pot ser un bug en hardy?

---

### Post by CarlesOriol on 2008-04-08
i amb un sleep encara més gran.

El fet que el proces trigui 1 minut des de que es connecta a que comença la copia tampo no t'afecta gaire. (total despres entre que comprova...)

---

### Post by patrickfromspain on 2008-04-08
tampoc.. el problema es que s'em munta despres d'executar l'script. L'ultim que he probat:

patrick@patrick-desktop:~/Escriptori$ cat script.sh
#!/bin/sh

sleep 60

if [ -d /media/cnmemoryUSB ]
then 
	/usr/bin/touch /home/patrick/Escriptori/MONTAT
else 
	/usr/bin/touch /home/patrick/Escriptori/NO_MONTAT
fi

patrick@patrick-desktop:~$ cat /etc/udev/rules.d/85-prova.rules
KERNEL=="sd[a-z]1", SYSFS{idVendor}=="08ec", ACTION=="add", RUN+="/home/patrick/Escriptori/script.sh"

Sense tocar res de l'udev el dispostiu es monta automaticament. Pero en quan hi poso l'script.. sempre em surt NO_MONTAT a l'escriptori... sleep 10, 30 o 60, es igual, simplement tarda més en montarse.

De moment he fet un script al disc dur que es diu autorun i alla faig l'rsync, tampoc es greu.

No es una cosa que em tregui el son.. pero em te intrigat, ja que sembla que faig el mateix que tu i res.. Per cert, ho he probat tant el disc dur extern com, aquesta ultima prova, amb el pendrive.

salut i gracies!

---

### Post by CarlesOriol on 2008-04-08
Jo ho tinc a la 99-udevmonitor... com que no ho tenia massa clar ho vaig possar a la última.

Prova-ho. 

Tampoc no crec que sigui per això però prova la connexió pel model tot i que em decanto més per la primera opció.

---

### Post by CarlesOriol on 2008-04-08
> **patrickfromspain said:**
> tDe moment he fet un script al disc dur que es diu autorun i alla faig l'rsync, tampoc es greu.

Ei. Aquesta si que es bona... no havia pensat mai en fer-ho així!

---

### Post by patrickfromspain on 2008-04-08
MOLTISSIMES GRACIES, CARLES!

Ja funciona tot perfecte. Sembla que això d'udev té molt en compte en quin ordre poses els parametres, d'altra banda no ho entenc. O potser devia tenir algunes opciones incompatibles o alguna cosa semblant, ja que juraria que no ho tenia massa diferent. Bé, el cas es que ja funciona.

Adjunto els arxius que he creat, per si a algú li semblen utils.

Salut!

PD: que tal una entrada al wiki sobre l'udev i les seves possibilitats? Algu s'animaria a ajudar-me?

---

### Post by CarlesOriol on 2008-04-08
L'udev és d'aquelles coses que quan vens de sistemes privatius ni t'imagines que poden existir.  I quan aconsegueixes fer-les funcionar per primer cop és realment màgic.

Si inicies el wiki m'apunto encantat a co&#320;laborar.

---

### Post by patrickfromspain on 2008-07-17
bé, encara que arribo molt tard i no es ben bé el que volia fer, he començat una entrada al wiki de com fer copies de seguretat utilitzant l'udev i rsync. 

[https://wiki.ubuntu.com/CatalanTeam/Recursos/Copies_de_seguretat](https://wiki.ubuntu.com/CatalanTeam/Recursos/Copies_de_seguretat)

De moment podeu veure que esta bastant incompleta, però espero poder anar millorant i omplint l'article. Qualsevol ajuda, addició i/o correcció serà, com sempre, molt ben rebuda.

salut!!!

---

### Post by papapep on 2008-07-18
Genial Patrick!!! Un tutorial molt bo! A veure si l'ampliem entre tots ;-)

---

### Post by patrickfromspain on 2008-07-20
En principi ho dono per finalitzat. A partir d'aqui, m'agradaria que us ho miressiu i hi fessiu les addicions/ correccions que cregueu pertinents o em diguem si creieu que s'hi ha d'afegir alguna coseta més.

salut!!

[https://wiki.ubuntu.com/CatalanTeam/Recursos/Copies_de_seguretat](https://wiki.ubuntu.com/CatalanTeam/Recursos/Copies_de_seguretat)

---

