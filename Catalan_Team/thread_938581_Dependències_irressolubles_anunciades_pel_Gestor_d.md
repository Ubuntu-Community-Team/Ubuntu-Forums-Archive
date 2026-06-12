---
title: "Dependències irressolubles anunciades pel Gestor de Paquets Synaptic"
date: 2008-10-05
forum: Catalan Team
---

### Post by Jayhawker on 2008-10-05
Hola, 

He reinstal·lat el 8.04.1 i m'està passant quelcom molt estrany. Quan entro al Gestor de Paquets Synaptic i vull instal·lar el"vlc" o el Flash Player o molts d'altres programets, com el Wine, o no me'ls reconeix o, per exemple, en el cas del visor de pel·lis vlc em diu que depèn del libdvbpsi4 i que aquest no és instal·lable. De fet en l'anunci d'això i en anglès diu que els packages següents tenen dependències irressolubles. 

Em queda molt limitat el sistema, perquè no puc entrar a la pàgina de TV3 ni puc veure cap clip.

Teniu alguna solució, sisplau? Sabeu què està passant. Mai abans no m'havia passat això. Al contrari, la primera vegada que vaig instal·lar el 8.04 fins i tot semblava més fàcil aconseguir coses pel Gestor. 

Merci, 

Jayhawker

---

### Post by CarlesOriol on 2008-10-05
Actualitza totes les fonts al synaptic abans d'insta&#320;lar. I fes una actualització de tots els paquets.

Si així i tot no et funciona copia'ns el teu /etc/apt/sources.list a veure que es pot fer.

---

### Post by Jayhawker on 2008-10-05
> **CarlesOriol said:**
> Actualitza totes les fonts al synaptic abans d'insta&#320;lar. I fes una actualització de tots els paquets.

Si així i tot no et funciona copia'ns el teu /etc/apt/sources.list a veure que es pot fer.

Merci per la resposta, però m'hauràs d'excusar: no sóc gaire més que un usuari d'ubuntu sense gaire coneixement del sistema. Si no és gaire feina, podries dir-me com s'actualitzen les fonts al synaptic (gairebé no sé què és això de fonts, aquí) i com s'actualitzen els paquets (suposo que són els mateixos que quan el 8.04 em funcionava plenament.)

he fet un reload i em surten uns missatges com si la connexió amb Ubuntu no fos possible ¿?

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-ca.bz2](http://es.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-ca.bz2)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-ca.bz2](http://es.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-ca.bz2)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-ca.bz2](http://es.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-ca.bz2)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-ca.bz2](http://es.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-ca.bz2)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-ca.bz2](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-ca.bz2)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-ca.bz2](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-ca.bz2)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-ca.bz2](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-ca.bz2)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-ca.bz2](http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-ca.bz2)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

W: No es poden descarregar alguns fitxers índex, s'han ignorat o en el seu lloc s'han usat els antics.

Sembla que hi hagi un problema de connexió, però jo bé que puc navegar.

Merci.

---

### Post by CarlesOriol on 2008-10-05
Crec que hi ha un problema temporal als servidors hispaniols. Segurament degut a l'intens moviment produit per la beta de la intrepid.

Ves al **synaptic >> paràmetres > fonts de programari **

i on diu Baixa de: 

tria el **servidor principal.**

---

### Post by Miquel Ubuntero on 2008-10-06
Bones.
Hi estic d'acord, si serveix d'algo.
Jo també tenia problemes d'actualitzacions i canvian les fonts del servidor hem va tirant be.
Salut!

---

