---
title: "[SOLVED] Problemes (accents, dvdcss...) en una ubuntu nova"
date: 2008-06-10
forum: Catalan Team
---

### Post by orestesmas on 2008-06-10
Hola companys/es,

Acabo de renovar la meva vella Debian Etch de casa per una flamant Kubuntu Hardy.

En general la instal·lació ha anat bé, i he pogut conservar totes les dades antigues, i això que l'estructura era més aviat complexa: el /home en un RAID1, el /opt en un LVM que agrupa diverses particions, el windows en un dels discs (jo no l'uso, malpensats!), etc.

He instal·lat a partir d'un CD **alternate install per AMD64**. Ho dic perquè potser aquesta pot ser una causa dels errors detectats.

Només 2 coses han fet ombra a tan magne sistema:

1) Misteriosament, el "locale" per omissió s'ha posat a **ca_ES-UTF-8@valencia** i, com a resultat, no anaven els accents. No és que m'importi massa anomenar valencià a la meva llengua, però una de dues: o bé els d'ubuntu arreglen el "locale" valencià, o bé s'asseguren d'escollir el català "universal" per omissió. Potser si algun MOTU llegeix això hauria de donar l'alarma...

2) No puc veure dvd xifrats. Encara que instal·li el paquet **libdvdcss2** segons el procediment usual (el d'executar un fitxer de /usr/share...), tots els reproductors insisteixen en dir que falla el desxifrat.

Llavors he buscat una mica i hi havia un web que suggeria instal·lar els w64codecs i el libdvdcss2 a partir dels supositoris de medibuntu. Doncs tampoc no ha funcionat.

Alguna idea?

---

### Post by papapep on 2008-06-10
Podries fer un cop d'ull a aquest fil:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html)

(kubuntaires, i a 64 bits....bah....només els falta ser dels que es dutxen cada dia...snobs... :-P)

---

### Post by orestesmas on 2008-06-10
Justament he seguit aquests passos de l'Ubuntu Geek per instal·lar el libdvdcss2, però tant és. EL tema del libdvdcss2 ja està solucionat. El problema era que jo tinc dos unitats de DVD: una lectora i una escriptora. Doncs bé, resulta que a l'espavilat de l'ubuntu se li ha acudit crear un enllaç /dev/dvd que apunta a l'unitat escriptora, enlloc de fer-ho a la lectora, i en intentar llegir el dvd fallava, però retornava un missatge dient que el suport per llegir dvd xifrats no estava instal·lat (llest, oi?)

El que m'ha despistat és que si intentava accedir al fitxer .VOB directament, es veia xifrat (àudio entretallat i vídeo amb molts artefactes) perquè el DeCSS no actuava. Jo em pensava que no actuava perquè estava mal instal·lat, i resulta que no actuava perquè deu ser el reproductor de DVD qui el crida en obrir un DVD sencer.

No sé si m'he explicat, però el cas és que aquest tema està liquidat.

---

### Post by Diegstroyer on 2008-06-11
Has provat d'anar al Suport d'idioma i canviar el valencià per l'andorrà? O potser et falten paquets d'idioma que es descarregaran quan i accedeixis per primera vegada.

Salut!

---

### Post by orestesmas on 2008-06-11
Hola Diegstroyer,

Potser no m'he explicat bé: Jo els paquets d'idioma els tinc tots ben instal·lats. El punt 1) no era un "problema" (en el sentit que no sabés com solucionar-lo) sinó una constatació per si a algú li passa el mateix.

Però el cert és que no he posat la solució: només cal anar al fitxer /etc/default/locale i editar allí el locale que es vol tenir per omissió (en el meu cas, treure el "@valencia" del final).

Després d'entrar de nou al sistema ja es té el locale correcte.

---

### Post by CarlesOriol on 2008-06-11
Per cert el locale andorrà ja funciona correctament en kde?

---

### Post by papapep on 2008-06-11
I jo encara diria més...KDE funciona correctament??? :-D

---

### Post by eselma on 2008-06-13
El KDE (3.5.9) al Kubuntu funciona com sempre, o sigui perfectament. Quan li toqui, el KDE 4.1 ho farà millor.

El problema amb el locale "ca_ES-UTF-8@valencia" també el vaig tenir al principi, i (sabent el que passava amb el ca_AD), un cop vista la sortida de $locale ho vaig arreglar anant a can /etc/default/locale i corregint-ho a ma. 

Potser s'hauria de posar algun avís a les PMF si no es pot adobar.

Potser el responsable del nyap (trasplantament de ca_AD?) és algun *blavero* dels que corren per aquí...

---

