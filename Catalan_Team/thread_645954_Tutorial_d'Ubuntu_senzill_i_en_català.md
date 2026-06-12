---
title: "Tutorial d'Ubuntu senzill i en català?"
date: 2007-12-20
forum: Catalan Team
---

### Post by idrojsnop on 2007-12-20
Bé, com que tampoc us vull atabalar gaire amb els meus problemes amb el Linux Ubuntu, perquè són masses, doncs m'agradaria saber si teniu cap tutorial que em pugui servir. Un toturial que m'expliqui quatre coses bàsiques per moure'm per Ubuntu, un tuturial per a gent com jo que no en té ni la més mínima idea, però que això sí, te ganes d'aprendre.

Per exemple, m'agradaria que em resolgués dubtes així com, instalar pluggins de vídeo, tot tipus de pluggins, amb el synaptic, instal·lar codecs, per poder llegir MP3, etc.

Com podeu veure, realment no en tinc ni la més mínima idea de fer anar el Linux, però suposo que algun dia tots hem començat, no?

Us dono les gràcies per endevant.
Una abraçada des de la Garrotxa.
Jordi.

---

### Post by papapep on 2007-12-20
Al wiki de l'equip: [https://wiki.ubuntu.com/CatalanTeam/Recursos](https://wiki.ubuntu.com/CatalanTeam/Recursos)
tens un petit recull d'adreces on trobar certa informació i algun d'aquests enllaços és, així mateix, un recull d'enllaços (recursiu, oi??).

Però, tot i això, donada la absolutament ingent quantitat de informació que existeix sobre Linux i Ubuntu a la xarxa, el punt de referència sempre seran els buscadors, i com a paradigma actual dels mateixos Google.

En català, com és evident, no trobaràs tanta informació. En castellà n'hi ha un munt i si et defenses llegint l'anglès ni t'ho explico.

També cal advertir, tot i que obvi no ho puc deixar de fer, que no tota la informació que es troba és d'una "solvència" o ofereix garantia suficient per a no fer cap destrossa al teu sistema, amb el qual cal tenir, cosa difícil al principi i motiu d'existència d'aquests fòrum per als més novells, un cert criteri (sobre Linux) per saber discriminar si el que t'aconsellen fer té lògica o és una bajanada.

---

### Post by torracastanyes on 2007-12-20
Com bé diu en Papapep, de documentació  n'hi ha molta i molt bona, però per començar a "fer peu" t'aconsello la de Ubuntu-es (això si, en castellà):

[http://doc.ubuntu-es.org/Portada](http://doc.ubuntu-es.org/Portada)

---

### Post by papapep on 2007-12-21
Acaben d'alliberar [un curs de Ubuntu Desktop]("https://wiki.ubuntu.com/Training") (per la 7.10) que es veu molt potent. 

Hàndicap per a molta gent: actualment només és en anglés, i no és molt fàcil que es traduexi, a no ser que s'hi impliqui molta gent, ja que són 414 pàgines el llibre de l'alumne i 400 i escaig més el del professor.

---

### Post by CarlesOriol on 2007-12-22
Aquest curs que diu en patatet és realment espectacular. Super recomanat.

---

### Post by lluisanunez on 2007-12-22
Com es pot descarregar això? No en un PDF de 72Mb., suposo.
M'he insta&#320;lat el bzr, i per si de cas Olive. Tinc compte a Launchpad. Però a l'anar a l'adreça bazaar.launchpad.net... em diu:

Not Found
The requested URL /00/00/1e/ce was not found on this server.

:confused:

---

### Post by papapep on 2007-12-22
Doncs si, són uns pdf's de 72 Mb... Ja us he dit que és extens :-)

Si et baixes les fonts del bazaar, tindràs els xml's, però no són massa "tractables" a no ser que els vulguis per modificar-ho o traduir-ho.

---

### Post by lluisanunez on 2007-12-22
Uau. Això és velocitat.
Doncs em pensava que amb el format docbook i l'XML es podria fer una cosa més manejable, per capítols...

---

### Post by papapep on 2007-12-22
Les fonts ja les tenen per capítols, però pensa que, segons he entès, aquest material és la base per a fer un curs (tot i que també serveix de llibre de consulta) o sigui que potser (només és una opinió personal) al crear el pdf ho han fet com "a més a més" sense pensar-s'ho massa si era manejable o no.

---

### Post by lluisanunez on 2007-12-22
Doncs jo els convidaria a pensar-s'ho una mica, i fer aquest curs 'available' per la gent, o sigui en format XML-HTML navegable. Els PDFs ja se'ls faria cadascú per a imprimir... (el meu s'ha encallat als vint-i-tants Mb, m'esperaré a ser a la uni per baixar-lo)
Això de la medalla ( = thanks) és nou, oi?

---

### Post by papapep on 2007-12-22
Ostres, me n'acabo d'adonar ara....primera notícia.
Veig que si hi cliques el que fas és constatar l'agraïment pel post al redactor...curiós :-)

Per cert, respecte l'html navegable, et refereixes a una cosa com això?:

[http://extralinux.net/files/cap1_curs_ubuntu.tar.gz](http://extralinux.net/files/cap1_curs_ubuntu.tar.gz)

---

### Post by lluisanunez on 2007-12-23
> **papapep said:**
> 
Per cert, respecte l'html navegable, et refereixes a una cosa com això?:
[http://extralinux.net/files/cap1_curs_ubuntu.tar.gz](http://extralinux.net/files/cap1_curs_ubuntu.tar.gz)

Exactament això, que és fàcil de fer des de l'XML (si hom aconsegueix les fonts que jo no he pogut)

---

### Post by orestesmas on 2007-12-23
Has de fer:
```

bzr co http://bazaar.launchpad.net/%7Ebilly-cina/ubuntu-desktop-course/ubuntu-desktop-course/

```

Després d'una bona estona de baixar, si el vols compilat t'has d'instal·lar el "dblatex" i les seves dependències (suposo que el texlive, no ho sé, jo ja el tenia instal·lat), entrar al directori principal i executar:

```
make booksg
```

El PDF generat són més de 70 MB, però això és perquè les (moltes) imatges que incorpora són en alta definició. Realment el procés de conversió XML -> PDF triga sorprenentment poc.

---

