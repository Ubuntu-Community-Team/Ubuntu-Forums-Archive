---
title: "Canviar el nom dels volums a &quot;Llocs&quot;"
date: 2008-05-10
forum: Catalan Team
---

### Post by Bensy on 2008-05-10
En instal·lar Hardy vaig fer 3 particions amb punt de muntatge dins de la meua carpeta d'inici, amb punt de muntatge en /home/bensy/Música, /home/bensy/Descàrregues/ i /home/bensy/Vídeos. El problema és que a "Llocs" i a l'escriptori m'apareixen com a "volum de mida tal", en comptes del seu nom, i encara que ja em sé quina és quina per l'ordre en que apareixen, seria més còmode que aparegueren amb el seu nom.

Per eliminar-les de l'escriptori vaig haver de fer que desaparegueren tots els volums, així que no m'apareixen els discos externs, pens i demés. I si pose els botonets al panel, hi ha un munt de discos i m'ocupa mitja barra. I em fa nosa haver d'anar-hi a /media cada vegada que he de desmuntar un dispositiu extern.

Com es pot fer que les particions del disc intern apareguen amb el nom del punt de muntatge? A Gutsy no tenia aquest problema.

---

### Post by CarlesOriol on 2008-05-11
Canvia el nom de la partició.

sudo tune2fs -L nomquevols /dev/lapartició

---

### Post by Bensy on 2008-05-12
bensy@lacabaretera:~$ sudo tune2fs -L Vídeo /dev/sda7
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block en intentar obrir /dev/sda7
Couldn't find valid filesystem superblock.

:( He fet res malament?

---

### Post by CarlesOriol on 2008-05-12
Si el sda7 no deu ser un ext3. tune2fs serveix per sistemes d'arxius ext3. Per canviar usar el nom en particions fat o ntfs pots usar windows, mtools o ntfs-tools

---

### Post by Bensy on 2008-05-12
> **CarlesOriol said:**
> Si el sda7 no deu ser un ext3. tune2fs serveix per sistemes d'arxius ext3. Per canviar usar el nom en particions fat o ntfs pots usar windows, mtools o ntfs-tools

És ReiserFS.

---

### Post by lpargemi on 2008-05-12
> **CarlesOriol said:**
> Canvia el nom de la partició.

sudo tune2fs -L nomquevols /dev/lapartició


Jo tenia un problema semblant, amb ext3, i això ha funcionat perfectament.

Agraït

Lluís

---

