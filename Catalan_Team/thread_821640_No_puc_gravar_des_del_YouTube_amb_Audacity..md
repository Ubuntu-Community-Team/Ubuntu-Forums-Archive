---
title: "No puc gravar des del YouTube amb Audacity."
date: 2008-06-07
forum: Catalan Team
---

### Post by bellit on 2008-06-07
Hola a tots,
Estic encantat amb Ubuntu 7, i em funciona tot correctament. L'única cosa en la que no me'n surto és gravar so de Youtube amb Audacity. Només he aconseguit de fer-ho amb L'enregistrador de so de gnome. Per tant dedueixo que amb Audacity també ha de ser possible.
La causa és que estava acostumat a l'Audacity de Windows on fàcilment seleccionaves el dispositiu d'entrada amb un ListBox, i a l'Audacity de Linux no sé com fer-ho.
Gràcies per endavant per la vostra ajuda.

---

### Post by orestesmas on 2008-06-08
Per respondre aquesta pregunta caldria saber diverses coses sobre com tens configurat l'àudio al firefox (assumeixo que uses firefox), i també quins dispositius d'enregistrament pot fer servir la versió d'audacity que tens instal·lada.

Tanmateix, no entenc perquè et vols complicar la vida d'aquesta manera, si de fet el so dels vídeos del youtube *ja està "gravat"*, només cal que et baixis el vídeo (amb el youtube-dl o similar) i extreguis l'àudio que porta (que és un mp3):

```

mplayer -dumpaudio -dumpfile audio.mp3 nom_del_video.flv

```

---

### Post by Miquel Ubuntero on 2008-06-09
Gracies Orestes.
A mi m'ha anat molt be això d'extreure l'àudio. No ho sabia!
Que guay :)

---

