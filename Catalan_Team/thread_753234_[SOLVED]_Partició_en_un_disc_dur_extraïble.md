---
title: "[SOLVED] Partició en un disc dur extraïble"
date: 2008-04-12
forum: Catalan Team
---

### Post by Joan Marc on 2008-04-12
Hola,
Tinc un disc dur extraïble, en format FAT32, el qual no em deixa col·locar-hi arxius més grans de 4GB.
He decidit fer-hi una partició NTFS perquè hi vull posar un Backup de WinXP, que ocupa 19GB.
El problema és, que des del gparted, em surt un cadenat al costat del nom del disc dur (adjunt), i no em deixa fer-hi cap operació.
Es pot desbloquejar? Com  ho puc fer?

Gràcies.

---

### Post by Joan Marc on 2008-04-12
Ja ho he solucionat... vaia tonteria.
S'havia de desmuntar des del gparted xD

---

### Post by Joan Marc on 2008-04-12
Abans de tancar el fil, quina diferència hi ha entre una partició principal i una partició estesa?

---

### Post by papapep on 2008-04-12
Les particions primàries (que no principals) són les bàsiques en que es parteix un disc dur (com ja saps). Com que d'aquestes no n'hi poden haver més de quatre en un disc, existeixen les exteses que fan de contenidor de les lògiques. Així doncs, les exteses (de les quals només n'hi pot haver una) fan de contenidor de tantes lògiques com calgui, que són les que realment es formaten al sistema de fitxers que ens cal, a fi de saltar-nos la limitació de les primàries.

---

### Post by Joan Marc on 2008-04-12
Ja ho entenc... així què és millor, crear una extesa i a dins creari una de lògica que n'ocupi tot el volum, o fer una de primària?

---

### Post by papapep on 2008-04-12
Això va a gust del consumidor, però jo no faria cap extesa si no faig curt amb les quatre primàries, cosa que només m'ha passat amb un servidor molt gran i que tenia un porró de particions.

---

### Post by Joan Marc on 2008-04-12
D'acort... ara mateix o faig...
Mmm... alhora de posar-hi el sistema de fitxers, no puc posar el ntfs... sols puc ext2, ext3, fat16, fat32, linux-swap, reiserfs i No formatada... Com li puc posar el sistema de fitxers ntfs?

Gràcies.

---

### Post by patrickfromspain on 2008-04-12
sudo apt-get install ntfsprogs

---

### Post by Joan Marc on 2008-04-12
Bee, gràcies als dos :)
Una última cosa, li puc posar nom a aquesta partició, i que aquest nom també surti al WinXP?

---

### Post by patrickfromspain on 2008-04-12
Si: sudo ntfslabel /dev/particio NOM

---

### Post by Joan Marc on 2008-04-13
No ho he provat perquè des del WinXP, posant "Canvia el nom", em detecta el nou nom des de l'ubuntu i altres WinXP.

Moltes gràcies a tots.

---

