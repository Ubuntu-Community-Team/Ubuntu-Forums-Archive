---
title: "Com escriure el Grub al disc dur principal"
date: 2008-04-22
forum: Catalan Team
---

### Post by sianeu on 2008-04-22
Fa poc vaig fer una instal·lació del Hardy (la beta, però no crec que tingui res a veure amb el problema) en un ordinador amb dos discs durs. El principal es Sata i l'altre (on vaig instal·lar el ubuntu) es IDE. El cas es que el Grub es va escriure al principi del IDE i, per tant, només arrancava si es canviava l'ordre d'arrancada a la bios.

Actualment el grub s'instal·la automàticament, i no se com dir-li que ho faci al disc Sata. Ara quan surti la versió definitiva ho intentaré altre cop. Com ho he de fer?

Salut

---

### Post by CarlesOriol on 2008-04-22
inicies amb un disc viu.

fas 
sudo grub

root (hd0,0)
-> disc i partició

setup (hd0)
-> escriu el grub al disc

quit

---

### Post by sianeu on 2008-04-22
Gracies. Però si faig una instal·lació nova, hi ha alguna manera de forçar a que s'instal·li al disc Sata (que deu ser el sda1) i no al IDE (hda1) que es on inastal·lo Ubuntu?

---

### Post by Curial on 2008-04-22
Sineu,

No sé si aquí trobaràs el que cerques, de fet hi ha força informació:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

salut.

---

