---
title: "[SOLVED] Visualitzar DVD amb menu"
date: 2008-06-03
forum: Catalan Team
---

### Post by Frealof on 2008-06-03
Iep!

Molt bones a tothom, l'altre dia volia mirar una peli que vaig llogar al videoclub. 

La qüestió es que quan la posava em trobava amb què el totem no la reproduïa. Seguint alguna indicació que vaig tornar per St.Google Gloriós vaig instal·lar el VLC i aquest si que em reprodueix els menús... però amb uns errors que crec que no hi haurien de ser, us adjunto una captura de pantalla que he fet avui que serà més clarificadora.

Alguna idea al respecte?

Salut!

---

### Post by CarlesOriol on 2008-06-03
Jo uso el xine i el desencriptador insta&#320;lat dels repositoris medibuntu.org

Però sembla un error del dvd físic.

---

### Post by Frealof on 2008-06-03
Iep!

Gràcies Carles,

He provat el DVD en un reproductor de la quinta del catapum que tinc per casa per comprovar si es veia bé i... si, es veu bé... L'he provat amb el Güindous i fa mal de reconèixer... però també es veu...

He instal·lat el Xine, però em surten un parell d'errors que tot i haver buscat pel Google, no he sabut solucionar. Tot i això seguiré buscant i si no trobo res ja us ho faria saber, ok?

Salut!

---

### Post by quitus on 2008-06-03
jo faig servir el VLC i em funciona correctament, això si, haig de desactivar els efectes visuals, però amb un amd 2800 sembla prou correcte.
Jo diria que es un problema de codecs, però es massa evident no?

salut

---

### Post by borgg on 2008-06-03
Hola!

El problema que deus tenir és que et falten els codecs per dexifrar el dvd (son així de cabrons i molts estan protegits)

En aquesta entrada al nostre blog solucionem el problema. Espero que et serveixi:

[http://joinfreesoftware.blogspot.com/2007/12/veure-dvd-en-ubuntu.html](http://joinfreesoftware.blogspot.com/2007/12/veure-dvd-en-ubuntu.html)


Salut!

---

### Post by Frealof on 2008-06-03
Iep!

Finalment si, era problema de codecs, com apuntava en Quitus i fent un cop d'ull al vostre blog, Borgg, he vist que em faltaven els w32codecs... i ara ja puc veure els DVD's amb el VLC sense cap mena de problema.

Tot i això... encara em queda el dubte de l'error que em donava amb el xine... Bé, haurem de seguir buscant ;)

En fi, moltes gràcies a tothom :)

Salut!

EDITO:

Fet! Per fer anar el Xine havia de crear un enllaç simbòlic entre /media/cdrom0 i /dev/dvd

:~$ sudo ln -s /media/cdrom0 /dev/dvd

Si us sembla, dono el fil per tancat.

salut!

---

### Post by CarlesOriol on 2008-06-04
Ara si que no ho entenc. Els codecs de w32codecs, el vlc crec que no els usa.

---

### Post by Frealof on 2008-06-04
Iep!

Doncs es l'única cosa que he instal·lat, la resta ja ho tenia... I a part de mi, aquest trasto no el toca ningú més...:confused:

Si voleu reobrir el fil per anar-ne parlant, per mi cap problema ;) L'he tancat perquè creia solventat "l'assuntu"...

Salut!

---

