---
title: "Reproducció d'un CD amb Amarok"
date: 2008-10-05
forum: Catalan Team
---

### Post by albert-I on 2008-10-05
Al voler reproduir un Cd amb l'amarok no m'ensenya els noms de les cançons i amb el VLC em passa el mateix, però amb Kaffeine, m'ho fa.

Que pot ser?

---

### Post by CarlesOriol on 2008-10-06
Els CDs de música normalment NO inclouen el nom de les cançons. (existeix un format però no acostuma a usar-se) 

El programa que dius segurament deu connectar-se a internet i en base al nombre de cançons i la seva duració cerca alguna equivalencia.

---

### Post by orestesmas on 2008-10-06
Bé, per mostrar-te els noms de les cançons tots aquests programes usen el sistema [CDDB]("http://en.wikipedia.org/wiki/CDDB"), que es basa en calcular un número ID únic per cada CD, i usar aquest número per consultar una base de dades on milers d'usuaris que tenen el mateix disc que tu han pujat prèviament la informació, que han extret (amb més o menys fortuna, tot s'ha de dir) del fulletó que acompanya al disc.

Si ni l'Amarok ni el VLC no t'ho fan, o bé no tens connexió a internet en aquell moment, o bé no has configurat els programes amb la URL del CDDB correcta.

En el cas de l'Amarok, ves a Arranjament -> Configura l'Amarok -> apartat "Motor" i allí on posa "Configuració del CD Àudio" posa-hi l'adreça d'un servidor CDDB. Jo hi tinc "freedb.freedb.org", al port 8880.

Al "directori cau CDDB" posa-hi un directori on es guardarà còpia de la informació que vas recollint, així pots usar-la més fàcilment o sense connexió a internet però, més important encara, pots compartir la informació entre programes i no duplicar-la.

Si el kaffeine t'ho fa, pots dir-li a l'Amarok que usi la caché del Kaffeine (de fet és la caché del xine, que és el motor que el kaffeine usa per omissió). Trobaràs on s'ho desa obrint el kaffeine i anant a Arranjaments -> Paràmetres del xine -> apartat "media" -> pestanya "Opcions avançades"

---

### Post by albert-I on 2008-10-10
Perdona la tardança, no m'he pogut mirar bé, fins avui. Doncs els paràmetres els tinc tal com dius, em sembla que son els que porta per defecte. Per tant,entenc que serà una altre cosa. 
El que ja no tinc tant clar, és el que pot ser

---

### Post by albert-I on 2008-11-13
Amb l'actualització pel mig i encara no funciona. Però hi ha el proper Amarok ja està amb beta. Algú l'ha provat? Alguna cosa a destacar?

---

