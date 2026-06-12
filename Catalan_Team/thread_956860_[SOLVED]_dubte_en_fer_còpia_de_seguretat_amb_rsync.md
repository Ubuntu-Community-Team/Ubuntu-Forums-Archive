---
title: "[SOLVED] dubte en fer còpia de seguretat amb rsync"
date: 2008-10-23
forum: Catalan Team
---

### Post by Pablitus on 2008-10-23
Wola! Bones!

Vull fer còpies de seguretat d'un seguit de carpetes a un disc dur extern. M'he estat mirant [això]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Copies_de_seguretat")(gràcies!!) i [això altre]("http://www.vicente-navarro.com/blog/2008/01/13/backups-con-rsync/"), però no sé si les conclusions que n'he tret són les correctes pel que vull fer 

La pregunta és si aquesta ordre és la correcta: ```
rsync -arv --delete /media/Terra/Banda/ /media/Zepelin/Banda/
```
El que vull és que esborri els fitxers i directoris del DESTÍ que hagi esborrat de l'ORIGEN
Amb els arxius d'àudio que tenen etiquetes ID3 que jo hagi canviat a l'ORIGEN m'els canviarà també a DESTÍ? És el que voldria.

Gràcies!!

---

### Post by papapep on 2008-10-23
Jo t'aconsello que creïs dues carpetes de proves, amb contingut no sensible, i que juguis amb l'ordre fins que et quedis tranquil amb el que fa. És un tema prou delicat com per assegurar la jugada. Crec que és la millor manera de fer-ho ;-)

---

### Post by Pablitus on 2008-10-25
Doncs bona, no se m'havia acudit i és ben sonzill. 

He fet carpetes de prova i l'ordre era bona, i ja l'he fet servir per fer les còpies de diferents directòris. Suposo que rsync es fixa en la data de modificació dels fitxers per saber que han canviat, i com que canviar les etiquetes ID3 d'un fitxer d'àudio suposa modificar un fitxer, pos sobreescriu l'antic a la còpia de seguretat amb la nova informació.

Gràcies!!

---

