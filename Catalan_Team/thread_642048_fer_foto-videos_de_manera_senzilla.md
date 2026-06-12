---
title: "fer foto-videos de manera senzilla?"
date: 2007-12-16
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-12-16
Bones!

Busco pel meu Ubuntu un programa per fer vídeos. És a dir, busco un programa senzill (en principi) on posi fotos, música de fons i surti un vídeo. I també un altre o el mateix on pugui agafar trossos de video ajuntar-los i remenar-los. I tot això des de fitxers, res de càmeres de video.
Suposo que com un Windows Media Marker o un Pinnacle (no és necessari tant) però pels pingüins...

Salut!

---

### Post by Tomàs M. on 2007-12-16
Per fotos he fet anar dvdslideshow; no té interfície gràfica però és molt fàcil de configurar i fer vídeos amb música.
T'adjunto un exemple per si al començament et costa agafar-li el "tranquillo":
```
firstday.mp3:1:fadein:0:fadeout:0
camins.mp3:1:fadein:0:fadeout:0
open.mp3:1:fadein:0:fadeout:0
background:1::black
fadein:2
title:4.26:Casament Eva & Manolo
crossfade:3
title:3:28/09/2007
background:0::black
fadeout:1
background:1
fadein:1
/home/tomi/eva_manolo/casament/fotos/img_2508.jpg:4.26
crossfade:1
/home/tomi/eva_manolo/casament/fotos/img_2509.jpg:4.26
fadeout:1
fadein:1

...

/home/tomi/eva_manolo/casament/fotos/img_2672.jpg:4.26
fadeout:3
fadein:2
title:6:Fet amb Gnu/Linux
crossfade:2
title:4: i DVD-Slideshow
fadeout:4
background:1

```

Per a vídeos només he utilitzat kino per a passar vídeos de la càmera al pc, però segur que per aquí et poden ajudar amb programes com cinelarra o devede

Sort, ganxet :-P

---

### Post by Miquel Ubuntero on 2007-12-16
Hei!
Tinc el que cerques. 
Jo faig un passes de fotos amb música molt fàcilment.
Es diu "ManDVD"
Si vols + info fes un cop d'ull a la pàgina núm 18 de la meva "Guia Ubuntu 7.04" que pots descarregar a la meva plana web 
[http://personales.ya.com/madroer](http://personales.ya.com/madroer)
Si tens dubtes d'instal·lació o de fer correr MandDVD pots fer-me un mail que amb molt de gust t'ajudaré.
Salut! i molt lliure soft ;)

---

### Post by orestesmas on 2007-12-16
Per edició no lineal de vídeo (tipus pinnacle):

- Kdenlive (una molt bona opció)
- Kino (permet captura directa de la càmera de vídeo DV)
- Jahshaka (interfície OpenGL, difícil de trobar paquet compilat)
-Cinelerra (molt potent, però complicat)

---

### Post by bikerbaixcamp on 2007-12-16
Ufff... necessito una interfície gràfica, de totes maneres, gràcies...

I bé, crec que la millor opció i el que busco més concretament és el Kdenlive. Ara bé, l'he buscat al ATP i eñ Synaptic; i he anat a la pàgina oficial i m'he trobat amb l'arxiu comprimit, que l'he descomprimit a la carpeta "sergi". A partir d'aquí no trobo cap icona d'instal·lació ni cap icona per executar el programa, com ho faig?

:) ;-)

---

### Post by lluisanunez on 2007-12-17
KDEnlive és als repositoris d'Ubuntu

---

### Post by papapep on 2007-12-17
A Gutsy hi és, al repositori Universe:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kdenlive&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kdenlive&searchon=names&subword=1&version=gutsy&release=all)

---

### Post by kukat on 2007-12-17
Jo l'estic instalant en aquestos moments: Aplicacions / Afegeix-Elimina i busques el Kdenlive. El marques i apliques els canvis...ja està!! 
Jo havia provat el Cinelerra (un poc complicat), i vaig a provar ara amb aquest... 
L'acabe d'obrir (s'ha instalat mentre escribia) I m'ha causat una bona impressió. Utilitzava molt el Pinnacle, però sempre peta, sempre té errors i sempre li passa alguna cosa, en Windows preferia el HT Videoeditor. Però ara ja tenim la solució, i sense cracks, serials ni tonteries.

---

### Post by bikerbaixcamp on 2007-12-17
> **kukat said:**
> Jo l'estic instalant en aquestos moments: Aplicacions / Afegeix-Elimina i busques el Kdenlive. El marques i apliques els canvis...ja està!! 


Això sona bé. El que passa es que tinc l'Ubuntu 7.04 i no si és per això o perquè he d'activar alguna cosa, però no em surt. A veure que hauria de fer...

Moltes gràcies a tots, poc a poc, vaig aprenent moltes coses! ;-)

---

### Post by kukat on 2007-12-17
Més fàcil encara!!

sudo apt-get install kdenlive

Ho poses en la terminal i llestos!!

---

### Post by papapep on 2007-12-17
Doncs no, a Feisty (la 7.04) no hi és el paquet als repositoris d'Ubuntu. En canvi a Gutsy, la actual estable, i a Hardy, la actual inestable, si que hi és:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kdenlive&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kdenlive&searchon=names&subword=1&version=all&release=all)

---

