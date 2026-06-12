---
title: "Ubuntu no arranca i fa un bucle mortal"
date: 2008-02-08
forum: Catalan Team
---

### Post by albello on 2008-02-08
Bones,

Açò és el que ha passat: quan apareix el logo d'Ubuntu amb la barra d'estat, en compte d'anar completant-se es para, i ix la pantalla en negre i les linies amb text, i apareix un percentatge. El percentatge va pujant però quan arriba al 18% es para. Quan reinicies l'ordinador passa exactament el mateix.

Jo estava fora i mon pare l'ha dut a l'informàtic, que li ha cobrat 35 € i li ha dit que hi havien uns errors a les comprovacions que fa linux cada cop que es reinicia, i que ho ha arreglat i també ha espaiat els xequejos periòdics (supose que això de "... has been mounted 46 times without being cheked, chek forced"). També li ha dit que esperant-se el temps suficient el percentatge s'hauria completat. Mon pare diu que va esperar uns cinc minuts.

En fi, el relat és un poc caòtic i jo no entenc res, però és tot el que he pogut sostreure-li a mon pare. A algú li ha passat alguna cosa semblant i em pot explicar què s'ha de fer?

---

### Post by papapep on 2008-02-08
Ostres, el títol del teu post m'ha fet pensar en el circ o en alguna película de'n Jaume Bond :-D

Bé, considerant la poca i "curiosa" informació que facilites, sembla que la verificació de les particions que es fa cada n cops al iniciar-se la màquina dóna algun error....per tant, es dedueix que tens algun problema físic al/als disc/discs, no??

Respecte el què heu de fer ara: estar molt atents a que no tornin a sortir problemes d'aquests, ja que, normalment, els error en la verificació són errors físics d'un disc que s'ha fet malbé. A cops també poden ser errors que queden per un tancament sobtat de l'ordinador per tall de corrent o similar, però no és habitual.

---

### Post by jodufi on 2008-02-08
Ara que comenteu això de les comprovacions d'arrencada, hi ha alguna manera que les faci menys sovint o saltar-ne una? Mira que arriba a ser odiós aquell dia que tens pressa i t'has d'esperar uns minuts extra perquè es dedica a comprovar els disc.

---

### Post by albello on 2008-02-08
Ostres, una altra vegada el disc dur. L'ordinador té any i mig i ja l'he canviat dues vegades. La primera vegada l'informàtic em va dir que l'ordinador no refrigerava gens bé. És un d'aquests menuts, amb el DVD en vertical i tota la pesca, i el ventilador està al davant. Potser és per això que es carrega els discs durs, perquè el tenim dies funcionant contínuament... Supose que si és un problema físic formatar el disc dur no servirà de res, no?

Respecte al tema de les comprovacions, l'informàtic ens ha dit que ens l'ha posat per a que la faja cada 1000 vegades (sospite que és l'únic que ha fet, a part d'esperar més que mon pare a que Ubuntu fera la comprovació), o siga que si que es pot canviar la freqüencià . El que no se és com. Ni per a què serveixen aquestes comprovacions.

---

### Post by papapep on 2008-02-08
> Ostres, una altra vegada el disc dur. L'ordinador té any i mig i ja l'he canviat dues vegades. La primera vegada l'informàtic em va dir que l'ordinador no refrigerava gens bé. És un d'aquests menuts, amb el DVD en vertical i tota la pesca, i el ventilador està al davant. Potser és per això que es carrega els discs durs, perquè el tenim dies funcionant contínuament...

Home, doncs si el dispositiu de l'ordinador que més calor disipa no es refrigera bé, és clar que pot ser una font de problemes :-) I més si el teniu 24/7 funcionant.

> Supose que si és un problema físic formatar el disc dur no servirà de res, no?

Jo el que faria és baixar-me una utilitat que solen tenir al web del fabricant del disc, sol ser una iso per a torrar a un cd i executar com a live-cd, i fer tots els test que pugui a fi de assegurar-me que és un error físic del dispositiu.

> Respecte al tema de les comprovacions, l'informàtic ens ha dit que ens l'ha posat per a que la faja cada 1000 vegades

Tu per a que el metge no et digui que estàs malalt retardaries les revisions de cada any a cada quaranta?? ;-) Doncs el cas és el mateix, si tens un problema al disc dur i no el detectes a temps per no fer les verificacions a l'arrencada, un dia et trobaràs sense tot el que hi tens dins. Potser, depenent de per a que el facis servir, no t'és important, però a nivell de feina, i fins i tot amb la quantitat d'informació que tinc als ordinadors de casa, no m'ho puc permetre.

> Ni per a què serveixen aquestes comprovacions.

Ja t'ho he contestat implícitament al darrer paràgraf: per a preveure problemes i evitar-los.

---

### Post by jaume69 on 2008-02-08
A mi em sembla que fa la comprobació cada vint **reinicis**,i em sembla que tarda 2 o 3 minuts com a molt.

---

### Post by papapep on 2008-02-08
Per defecte, si no recordo malament, està previst a cada 30 inicis, i trigar triga en funció de lo gran que és el disc, del sistema de fitxers que utilitzi, del tipus de dades que s'hi desin i d'altres factors físics com ara el bus de comunicacions, etc.

Canviar-se es pot canviar a voluntat però, excepte casos especials, no hi trobo massa sentit a modificar-ho.

Tot i això, la ordre de terminal [tune2fs]("http://blog.mob1970.org/?p=88") és la que s'encarrega de configurar aquest tema.

PS: Són 35 leuros :-P

Per cert, JAUME69, si et triga 2 o 3 minuts és que deus tenir un disc molt gran, molt lent o les dues coses, ja que és molt temps.

---

### Post by albello on 2008-02-09
Enterat!

PS: porte sis anys sense anar al dentista i ja són sis anys amb les dents perfectes... :)

---

