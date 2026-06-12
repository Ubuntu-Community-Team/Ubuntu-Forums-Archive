---
title: "No em funciona el so"
date: 2008-10-24
forum: Catalan Team
---

### Post by lo gambusí on 2008-10-24
Salut!

D'uns dies ençà no em funciona el so. Quan poso a reproduir un arxiu amb l'amarok, o un vídeo del youtube, o el que sigui en lloc d'escoltar-se el so es sent un soroll molt estrany i fluixet.

He anat a Sistema/Preferències/So i he canviat l'*ALSA* per *HDA INTEL ALC883 Analog (OSS)* (pitjant al botó de prova sonava bé) però segueix sense funcionar.

Alguna idea?

---

### Post by grundt on 2008-10-24
A mi em passa lo mateix des que vaig instal·lar la última versió d'ubuntu.

Si tinc l'Amarok no em reprodueix el so del youtube i a l'inrevés crec que 

es penja l'Amarok.

Més avall hi ha un post que també parla del conflicte entre Amarok i flash?

De fet jo des que tinc l'ultima versió, no puc escoltar bé les pelis que em 

baixo, ja que va fent uns tallets cada deu segons, però això ja és un altre 

post.

---

### Post by lo gambusí on 2008-10-24
A mi directament ni youtube ni amarok :(

---

### Post by papapep on 2008-10-24
Si no vaig errat, el tema d'audio no és pas el meu fort, Hardy incorpora com a novetat el sistema d'audio Pulseaudio. Podeu provar a ficar-lo com a sistema predeterminat a Sistema > Preferències > So, a veure si us funciona millor.

---

### Post by Pablitus on 2008-10-25
Crec que el sò és un dels temes delicats a l'Ubuntu. Jo també hi vaig tenir problemes, però per sort, com que molta gent s'hi ha trobat hi ha molta informació en blogs i fòrums. 

Suposo que teniu problemes diferents **Lo Gambusí** i en **Grundt**. Sobre el tema d'escoltar múltiples sons a l'Ubuntu hi ha bastanta info a la xarxa.

Us deixo pag. que en parlen, jo ho vaig solucionar provant el que proposaven:

[http://ubuntulife.wordpress.com/2008/08/18/solucionar-problemas-de-pulseaudioflash-en-ubuntu-hardy-heron-por-fin/]("http://ubuntulife.wordpress.com/2008/08/18/solucionar-problemas-de-pulseaudioflash-en-ubuntu-hardy-heron-por-fin/")
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
[http://redavalon.blogspot.com/2007/03/multiples-sonidos-en-ubuntu.html]("http://redavalon.blogspot.com/2007/03/multiples-sonidos-en-ubuntu.html")

Per si ajuda, a les preferències de sò jo ho tinc tot a "servidor de sò Pulse Audio", però en "detecta automàticament" també hauria de funcionar. I els paquets "pavucontrol", "padevchooser", "paprefs" i "pavumeter" instal·lats. 

Sento no poder ser de més ajut, però no controlo gaire i vaig resolent problemes amb el mètode assaig/error fins que em funciona, de vegades sense saber del tot què faig. Us recomano fer còpies de seguretat en editar fitxers de configuració i parar atenció a quins paquets instal·leu i desinstal·leu per poder tornar enrera en un moment donat o per aïllar els problemes.

Sort! I si ho solucioneu i dieu com seria fantàstic!

---

