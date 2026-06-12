---
title: "Possibles formats per a un llapis USB"
date: 2007-12-25
forum: Catalan Team
---

### Post by giorgiograppa on 2007-12-25
Bons torrons!

Espere que no estigueu massa atipats de cava, a veure si em podeu donar un cop de mà.

El cas que vull que estrenar un llapis USB de 8 GB que m'acabe de regalar, i la primera "perreria" que li vull fer és formatar-lo per anar fent proves amb diverses instal·lacions Linux (la SLAX que tinc a l'altre llapis ja em resulta massa fàcil i tinc ganes de complicar-me la vida).

El dubte existencial és: quins formats natius Linux suporten aquestes unitats? He fet una recerca amb el Google i sembla que només admeten FAT16 i FAT32. Algú sap si es poden formatar com a EXT3 o algun altre sistema més "pingüinaire"?

He observat que el GParted no m'ofereix la llista completa, sinó que només em deixa triar entre: ext2, ext3, fat16, fat32, jfs, linux-swap, ntfs, reiserfs, xfs. És fiable l'opinió del GParted? Són realment aptes aquests formats per al llapis de memòria?

Ale, bones festes a tots, i compte amb el colesterol.

---

### Post by papapep on 2007-12-25
Un llapis de memòria USB pel linux és un sistema d'emmagetzematge normal i corrent (com un disc dur qualsevol), i el pots formatar en qualsevol dels sistemes de fitxers habituals: fat, ntfs, ext2, ext3, etc...

---

### Post by eselma on 2007-12-25
No sé si això serveix per al cas del "llapis" o "clauers" de memòria flash; en tinc un parell i la veritat és que es van quedar amb el format original, VFAT (el més gran és de 2GB); com que només hi poso fitxers de dades, no em preocupa el propietari ni els permisos; els estableixo en tornar-los al disc dur, si cal. El VFAT té l'avantatge (potser l'únic) de que és reconegut per un sistema *Hasefroch*, si convingués.

Però tinc una petita unitat de 40 GB externa (usa un disc dur de 2,5", del tipus dels ordinadors portàtils); aquest l'uso si cal fer una* transfusió* més seriosa entre màquines. Ve alimentat en corrent i dades per un parells de connectors USB. No cal dir que aquest està formatat en *ext3*, i no he tingut cap problema fins ara. 

Jo en el teu cas (si no necessites compatibilitat amb la zona fosca) provaria de formatar-lo en *ext3* o semblant (no crec que usis *ReiserFS o XFS*) a veure que passa; si no respon com vols (no hi veig raó aparent, si és una memòria flash a l'engròs -*bulk *o *raw*- amb la seva petita interfície de firmware) sempre et queda el recurs de formatar-lo en *fat32* (o *NTFS*, si vols; potser més arriscat).

Apa, que ja veig que dins el tió no hi cap maquinari de gaire embalum, encara que tingui molts GB.

---

### Post by giorgiograppa on 2007-12-25
Gràcies, Papapep i Eselma! (Per cert, què feu davant de la pantalla a estes hores, el dia de Nadal? ;-) )

Pocs minuts abans de les vostres respostes (tan detallades com sempre), havia trobat un post sobre com instal·lar Ubuntu sobre un llapis USB [(http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar")); allí s'indicava que calia formatar el llapis a ext2, d'on ja m'he pogut imaginar el que em deia en Papapep. (Per cert, que no he pogut accedir a la traducció que en va fer en RainCT, però ja ho tornaré a provar.)

Impacient com sóc, ja l'he formatat (3 GB fat32, per poder intercanviar amb el costat fosc; 4 GB ext32, per instal·lar-hi un Linux "amb tota la barba", i 515 MB de swap; sí, ja sé, això no suma 8 GB...), i sembla que està bé de salut.

Ale, ja tinc entreteniment per a demà. Ja aniré fent resums al meu [bloc]("http://laventuradelpingui.blogspot.com/"), per si algú més té curiositat.

Gràcies per l'ajuda, i bons torrons!

---

### Post by giorgiograppa on 2007-12-25
Olé! Olé! La [traducció]("http://rainct.bloc.cat/post/8808/149292") d'en RainCT sobre com instal·lar Ubuntu al llapis USB ja està accessible! Ja tinc més material per fer-hi experiments!

---

