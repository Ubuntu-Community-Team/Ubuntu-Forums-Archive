---
title: "Comprobar els components de la CPU"
date: 2008-09-09
forum: Catalan Team
---

### Post by Daerun on 2008-09-09
M'agradaria saber si hi ha alguna manera de conèixer detalls sobre el tipus de hardware que tinc instal·lat al meu PC. Anant a Sistema > Administració > Monitor del SIstema, es pot comprobar la quanitat de RAM, y el model y velocitat del processador, però per exemple no s'hi troben detalls sobre la RAM (si és DDR o DDR2, etc) o d'altres components de l'ordinador.

---

### Post by patrickfromspain on 2008-09-09
sudo apt-get install dmidecode
sudo dmidecode

Busca en la sortida i hi trobaras informacio de la ram instal·lada a cada socol.

salut

---

### Post by Daerun on 2008-09-11
Això está força bé, gràcies :D S'hi pot introduir algun parámetre perquè doni més detalls? Es que no m'especifica si la meva RAM es DDR o DDR2 :P
De totes maneres això és el que buscaba.

---

