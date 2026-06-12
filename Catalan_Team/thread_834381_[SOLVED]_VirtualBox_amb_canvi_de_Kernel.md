---
title: "[SOLVED] VirtualBox amb canvi de Kernel"
date: 2008-06-19
forum: Catalan Team
---

### Post by oriolsbd on 2008-06-19
Hola a tothom.

Tinc instal·lat el VirtualBox (la versió completa, no la OSE). Com que aquesta versió no està als repositoris d'Ubuntu, per instal·lar-la t'has de baixar de la web de VirtualBox el fitxer ".deb" corresponent. M'he trobat amb el problema que, quan canvia la versió del kernel d'Ubuntu deixen de funcionar les màquines virtuals, i donen el mateix error que ja ha sortit en algun fil anterior:
[http://img372.imageshack.us/my.php?image=capturavirtualboxerrorqq8.png](http://img372.imageshack.us/my.php?image=capturavirtualboxerrorqq8.png)

En els fils anterior, sempre es parlava de la versió OSE, i la solució era esperar a què sortissin els mòduls per al nou kernel (i mentre no sortissin, engegar l'ordinador amb la versió antiga del kernel si saps que vols treballar amb VirtualBox).

Per a la versió completa, el que jo estic fent és desinstal·lar el VirtualBox (sense purgar els fitxers d'usuari, clar, per no perdre les màquines virtuals), baixar-me de nou el fitxer ".deb" i tornar a instal·lar.

Algú ho fa d'alguna manera més "neta"? Està en algun repositori la versió completa de VirtualBox?

Gràcies.

---

### Post by patrickfromspain on 2008-06-19
en un terminal: sudo /etc/init.d/vboxdrv setup

---

### Post by Diegstroyer on 2008-06-19
Segur que no tens la versió OSE? Aquest error correspon a la versió esmentada, és molt estrany... però si tens la privada, la solució te la donen a dalt.

---

### Post by oriolsbd on 2008-06-19
Segur que no tinc la OSE. És que estava treballant des d'un PC amb Windows, i no tenia l'error a mà i he enganxat el mateix enllaç que havia penjat un company en aquest fòrum. :P

Ara provaré la solució que ha comentat el Patrick.

Gràcies.

---

### Post by jodufi on 2008-06-19
De fet, si executes el virtualbox des d'un terminal allà et diuen que hi ha un problema i et proposen la solució.

La solució és la que ja ha dit en patrick

---

### Post by oriolsbd on 2008-06-20
Ja em funciona, moltes gràcies. :-)

---

