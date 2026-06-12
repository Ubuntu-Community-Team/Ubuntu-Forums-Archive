---
title: "[SOLVED] Adaptador USB de xarxa inalàmbric AMPER de telefònica"
date: 2008-02-13
forum: Catalan Team
---

### Post by Frealof on 2008-02-13
Hola a tothom! :) 

Ara fa poc he canviat el PC d'habitació, i com que no puc passar cables amunt i avall, vaig decidir que provaria de fer servir els adaptadors USB de xarxa (juntament amb el router Zyxel) que em varen "regalar" els de la telefònica al contractar el servei ja fa un temps, i així poder tenir una petita xarxa domèstica a casa.

Vaig estar mirant diversos posts i en vaig trobar un que segons deia permetia instal·lar els Drivers de l'adaptador USB AMPER. Dit i fet, instal·lo Ndiswrapper via Synaptic; Executo el programa; Busco el controlador a media/cdrom1/Setup/Win2KXP/wlannic.inf; faig clic i Oh, sorpresa! Funciona! Tinc el driver instal·lat, però hi ha un petit problema i es que el led de l'aparell ni s'encén. 

Faig lsusb per veure si realment el tinc connectat i... em surt això.

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 001 Device 003: ID 09aa:3642 Intersil Corp. Prism 2.x 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  

Bé, tot i no apareixer com a AMPER sembla que l'aparell esta endollat i detectat, peròò... com es que no va? alguna idea?

Gràcies per endavant!

---

### Post by Frealof on 2008-02-13
Hola de nou! :)

He trobat part de la solució en aquest post 

[http://www.ubuntu-es.org/index.php?q=node/51144](http://www.ubuntu-es.org/index.php?q=node/51144)

Ara el led ja esta actiu i amb wifi-radar em detecta la meva xarxa inalàmbrica i les dels veïns amb la qual cosa sembla que tot hauria de rutllar, però no... He seguit els passos allà indicats i bé, hi ha alguna cosa que falla perquè no em puc connectar a la xarxa. Seguiré buscant... però si teniu alguna idea, serà molt benvinguda!

Salut!!

---

### Post by Frealof on 2008-02-13
Solucionat!!! :)

He sortit de la sessió; Apagat el PC; Desconnectat el cable de Xarxa que tenia posat i BINGO!! Quan he engegat el PC de nou se m'ha connectat sense problemes.

Espero que el Link que he deixat més amunt i que a mi m'ha servit pugui ser útil a d'altres usuaris/es que s'hagin trobat amb la mateixa situació que jo. ;)

Salut!

EDITO: Ara amb l'actualització a Hardy Heron, el dispositiu s'instal·la i esta operatiu des del primer moment ;)

---

