---
title: "problemes amb flash al firefox 3"
date: 2008-06-25
forum: Catalan Team
---

### Post by ferreret on 2008-06-25
Hola, tinc problemes amb el Firefox 3 i el flash player. per exemple si vaig al youtube he de clicar sobre el video per poder veure'l cada vegada, i la meitat de cops queda en blanc i no es veu el video. com ho puc arreglar? vaig instalar el paquet d'adobe del flash

---

### Post by oriolsbd on 2008-06-26
Hola.

Des de Synaptic has d'instal·lar el paquet "flashplugin-nonfree". Desinstal·la el "swfdec-mozilla" (si el tenies instal·lat).

Salut!

---

### Post by ferreret on 2008-06-26
> **oriolsbd said:**
> Hola.

Des de Synaptic has d'instal·lar el paquet "flashplugin-nonfree". Desinstal·la el "swfdec-mozilla" (si el tenies instal·lat).

Salut!

Precisament és així com dius que ho tinc instalat

---

### Post by dafaktor on 2008-07-01
Una mica més de llenya: a mi no se'm queda en blanc sinó que moltes vegades, en clicar al play d'un vídeo en flash, es tanca el firefox directament. Si llavors el torno a obrir moltes de vegades reprodueix correctament.

També tinc instal·lat el flashplugin-nonfree.

Idees?

---

### Post by fonde on 2008-07-07
> **ferreret said:**
> Hola, tinc problemes amb el Firefox 3 i el flash player. per exemple si vaig al youtube he de clicar sobre el video per poder veure'l cada vegada, i la meitat de cops queda en blanc i no es veu el video. com ho puc arreglar? vaig instalar el paquet d'adobe del flash


eis!a mi em passava igual.
ho he solucionat anant al **FIREFOX>EINES>COMPLEMENTS** i a la pestanya de EXTENSIONS inhabilites el flashblock,que és una extensió de Firefox que bloqueja la reproducció de continguts Flash.

espero que sigui això!:wink:

saluuut

---

### Post by dafaktor on 2008-07-07
> **fonde said:**
> eis!a mi em passava igual.
ho he solucionat anant al **FIREFOX>EINES>COMPLEMENTS** i a la pestanya de EXTENSIONS inhabilites el flashblock,que és una extensió de Firefox que bloqueja la reproducció de continguts Flash.

espero que sigui això!:wink:

saluuut

Doncs no la tinc pas jo aquesta extensió.... :(

---

### Post by fonde on 2008-07-07
> **oriolsbd said:**
> Hola.

Des de Synaptic has d'instal·lar el paquet "flashplugin-nonfree". Desinstal·la el "swfdec-mozilla" (si el tenies instal·lat).

Salut!

mmm i pot ser que tinguis algun paquet relacionat amb el gnash instal·lat? si és així carda'ls tots a la foguera...busques gnash al synaptic i a fe neteja...

tens el libflash-mozplugin instalat?(si no li tens instala'l)

diga'm el què,estaré per aquí un ratet

---

### Post by Kosimo on 2008-07-07
Hola!

Per què no probeu d'instal·lar-vos l'última Beta 2 del que serà Flash Player 10? Tot i no ser espectacular té un rendiment millor que tots els anteriors, i un consum de la CPU inferior.  

Aquí hi ha instruccions sobre com instal·lar-ho.
[http://ubuntuforums.org/showthread.php?t=795019](http://ubuntuforums.org/showthread.php?t=795019)

Sort!

---

### Post by orestesmas on 2008-07-07
> **fonde said:**
> mmm i pot ser que tinguis algun paquet relacionat amb el gnash instal·lat? si és així carda'ls tots a la foguera...busques gnash al synaptic i a fe neteja...


Amb tota la delicadesa de què sóc capaç, he de dir-te que caldria que fossis més curós a l'hora de llançar improperis immerescuts sobre el gnash. EL gnash és un dels intents més seriosos i lloables que disposem per tal de poder-nos alliberar d'aquesta merda infecta i privativa que s'anomena Adobe Flash player per Linux.

Que el gnash tingui encara problemes per reproduir alguns vídeos del youtube no es pot atribuir a la seva mala qualitat, sinó al fet que encara es troba en fase "beta", i no es pot jutjar amb els mateixos paràmetres que s'usen per a una aplicació ja acabada.

D'altra banda, has provat de reproduir vídeos del youtube a pantalla completa amb el plugin privatiu de flash? L'ordinador s'escalfa tant que s'hi podria fer un ou ferrat al damunt. Si això és un exemple de programa que funciona bé, ja em diràs...

Gnash està programat per una autèntica llumenera del programari lliure, en [Rob Savoye]("http://en.wikipedia.org/wiki/Rob_Savoye"), que fa més de vint anys que està ficat en tota mena de projectes de programari lliure (el gcc entre d'altres), i que encara té temps per dedicar 5 mesos de la seva vida a anar a ajudar els damnificats de l'huracà Katrina.

Malgrat tot, la solució definitiva a la reproducció de continguts web multimèdia sobre GNU/Linux no vindrà del gnash per si sol, sinó que començarà a ser una realitat quan els usuaris exigim que els formats multimèdia al web siguin estàndards oberts i lliures de patents.

---

### Post by fonde on 2008-07-08
> **orestesmas said:**
> 

D'altra banda, has provat de reproduir vídeos del youtube a pantalla completa amb el plugin privatiu de flash? L'ordinador s'escalfa tant que s'hi podria fer un ou ferrat al damunt. Si això és un exemple de programa que funciona bé, ja em diràs...



sento haver apartat el gnash de la meva vida així...però de moment només he aconseguit reproduir videos en flash amb el flash d'Adobe...ja m'agradaria que el meu ordinador no cremés tant...:(

---

### Post by CarlesOriol on 2008-07-09
Ores

Malgrat que el flash no sigui un format lliure, val a dir que el mes passat van lliurar les especificacions. Això vol dir que l'empresa seguirà controlant el format i tindrà el monopoli de les especificacions i canvis. 

Però crec que es una bona noticia per projectes com el gnash.

---

### Post by orestesmas on 2008-07-09
Tens raó, però això ja ho sé. Justament me'n vaig fer ressò al meu bloc no fa gaire.

Però aquí estàvem discutint bàsicament sobre implementacions, no pas sobre les especificacions directament. I és evident que fins ara (i no crec pas que això canvïi a mig termini) les implementacions privatives del Flash per GNU/Linux són nefastes. Jo crec que només tindrem un bon plugin de flash pels navegadors si s'implementa en programari lliure.

I en aquest sentit és evident que l'obertura de les especificacions del flash farà que el gnash avanci més de pressa, però el fet que Adobe segueixi controlant les especificacions és un problema. Fa que sigui molt difícil fer programari lliure que suporti totes les especificacions. És llarg de discutir però és el mateix cas que el PDF: A data d'avui encara no disposem de programari lliure per explotar totes les característiques del PDF (com ara els formularis i l'edició).

Esperem que això del PDF canvïi ara que [ja és estàndard ISO]("http://www.iso.org/iso/pressrelease.htm?refid=Ref1141"), una notícia molt recent (1 de juliol) i que ha passat força desapercebuda.

Per tal que puguem estar tranquils amb el Flash, aquest també s'hauria de convertir en estàndard ISO, fora del control exclusiu d'Adobe, i alliberar-lo de patents. Qualsevol altra cosa em sembla que només són maniobres per intentar mantenir una quota de mercat que potser veuen perillar en un futur, qui sap si amenaçada per iniciatives com la de la Wikipedia, que sembla que vol posar en marxa un portal per compartir vídeos que funcionarà exclusivament en Theora/Vorbis.

Mantenir la quota de mercat... Us sona també que Microsoft ha anunciat recentment un plugin per tal que el seu Office pugui llegir i escriure OpenDocument? La jugada és clara: si OpenDocument és estàndard i els governs s'hi estan abocant, almenys que els documents els generin amb Office enlloc d'OpenOffice. Perdran el monopoli però amortiran el cop...

(Uff, quin rotllo...)

---

### Post by SiscoGarcia on 2008-07-09
> **orestesmas said:**
> ...

(Uff, quin rotllo...)

Cap rotllo Orestes, em sembla molt didàctic, que és el que ens cal a tots plegats, és a dir, saber perquè fem allò que fem.

Gràcies pel que ens has explicat, de debò ;)

---

### Post by jaume69 on 2008-07-10
jo el que he vist és que quan veig alguns vídeos diferents a **Youtube** amb **Firefox** i **flash-nonfree**,s'em tanca el **Firefox**.
No he provat instal.larlo de la pàg.**Adove**,pot ser va millor. ¿?

---

### Post by pespin on 2008-07-11
> instal.larlo de la pàg.Adove,pot ser va millor. ¿?

Si t'hi fixes al instal·lar/actualitzar el paquet flashplugin-nonfree el que fa l'instal·lador és descarregar l'arxiu de la pàgina d'Adobe, ja que diria que no poden tenir-lo als repositoris propis d'ubuntu per temes legals ;)

---

### Post by jaume69 on 2008-07-14
[QUOTE="pespin"]Si t'hi fixes al instal·lar/actualitzar el paquet flashplugin-nonfree el que fa l'instal·lador és descarregar l'arxiu de la pàgina d'Adobe, ja que diria que no poden tenir-lo als repositoris propis d'ubuntu per temes legals [/QUOTE]

Així el **Flash** dels repositoris és el mateix que la plana web **Adove**?:confused:

---

