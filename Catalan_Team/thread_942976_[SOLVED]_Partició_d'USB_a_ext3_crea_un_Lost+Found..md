---
title: "[SOLVED] Partició d'USB a ext3: crea un Lost+Found."
date: 2008-10-09
forum: Catalan Team
---

### Post by LitusMayol on 2008-10-09
Bones familiaa!

En un pen que tinc hi he fet una partició de ½Gb a *fat32* i els 3½Gb que restaven a*ext3*.

Doncs a la partició d'*ext3* m'hi crea (ell solet, el **Gparted**) una "*Lost+Found*" que assegura que "*No teniu el permís necessari per poder veure el contingut de «lost+found».*". Per tan com és obvi ni m'ha deixat esborrar-la ni excrutar-la. 

Amb "*gksu nautilus /media/disk-1*" m'ha deixat accedir-hi comprboar que no hi havia re i eleminar-la. Però per sorpresa meva després d'haver-la eliminat (fins hi tot del *.trash *que es crea) encara hi havia part de la memòria ocupada.(veure adjunt)

Algú sap perquè passa i com puc solucionar-ho? 
Merci!

---

### Post by indiosincracia on 2008-10-10
No t'aconsello que el treguis, Fsck guarda aquí els arxius que recupera en cas de catrastofe (en cas que es pengi falta de corrent etc... el disc dur), cada partició te el seu lost+found


més info:
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.htm](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.htm)

---

### Post by patrickfromspain on 2008-10-10
es normal que hi sigui aquesta carpeta, es un tema del sistema de fitxers. Per a utilitzar millor l'espai, hauries de provar amb d'altres sistemes, com ara xfs o jfs, que em sembla que utilitzen mes bé l'espai.

salut

---

### Post by LitusMayol on 2008-10-11
Treballant amb el **GParted** no m'ha deixat fer una partició amb *xfs *o *jfs*. Al final l'he deixat a *.ext3* i amb la carpeta! ;)

Merci a tots. Almenys he après cosetes!

---

### Post by patrickfromspain on 2008-10-11
em sembla que t'has d'instal·lar els paquets xfsprogs i jfsutils.

salut

---

### Post by LitusMayol on 2008-10-12
En efecte mestre.

Em faltaven aquest dos paquets, ara ja puc.
Merci!

---

