---
title: "Sugerrències per a la &quot;completa(??)&quot; instal.lació de KDENLIVE?"
date: 2008-09-19
forum: Catalan Team
---

### Post by kukat on 2008-09-19
Tinc instal.lat el KDENLIVE. Però he vist a la seua web que hi ha una instal.lació que compila tot el necessari (no se si m'explico, la veritat es que es un poc confús...)

[http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing](http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing)

La part de "Compiling kdenlive & ffmpeg & mlt together - the easy way", on es dona un script per instalar tot el necessàri (supose que per a que funcione el millor possible, amb totes les llibreries i tots els avantatges...) 

El problema es que, al exportar un video a .mpeg, .avi, .mov, o el que siga, el so no s'escolta bé. S'escolta a "trompicons". I he provat en "preferències" de canviar el hardware d'àudio (Alsa, OSS, etcètera...) però s'escolta igual o pitjor...

Doncs això, que l'script pareix que no funciona (hi falten algunes llibreries i coses així, supose per que estarà un poc "desfasat")...Algú ha instal.lat el KDENLIVE amb l'script o d'alguna forma similar, o sap per què pot escoltar-se a "trompicons" ????' 

Gràcies! Es una llàstima per què tinc un video ja fet, i no voldria tindre que anar-m'en al Windows.
Salutacions!!!

---

### Post by orestesmas on 2008-09-24
Ara fa algun temps que no m'ho he mirat (d'abans de l'estiu). El problema del kdenlive és que el desenvolupament de la versió per KDE3 ha quedat aturat perquè els programadors estan concentrant els seus esforços en la versió per KDE4, que probablement sortirà amb el KDE4.2, al gener.

Mentrestant, com tu dius, si vols la darrera versió l'has de compilar, però com que les dependències són una mica rotllo, hi ha aquest script que teòricament ho fa tot.

Quan vaig provar l'script també va petar en algun punt, i fins i tot ho vaig expolicar als desenvolupadors, que em van dir que s'ho mirarien. Però com ja t'he dit, després d'això no ho he tornat a provar.

A veure si més tard et busco la URL del bug report i en pots treure l'aigua clara tu mateix.

---

### Post by kukat on 2008-09-24
Gràcies!!!! La veritat es que el Kdenlive està molt molt bé. Però em surt el problema de l'audio una vegada acabat tot..Gràcies!!!

---

### Post by orestesmas on 2008-09-24
No ho acabo d'entendre... si dius que l'script que el compila no acaba de funcionar bé, i que peta, aleshores... com és que pots editar un vídeo?

Sigui com sigui, la URL de què et parlava abans (per si t'ho vols mirar) és aquesta:
[http://www.kde-apps.org/content/show.php/Kdenlive+Builder+Wizard?content=85826](http://www.kde-apps.org/content/show.php/Kdenlive+Builder+Wizard?content=85826)

Quant al problema del so a "trompicons", caldria que fessis cinc cèntims dels formats i còdecs que has emprat. A vegades alguns còdecs no són massa òptims per segons quins formats i passen coses estranyes. Quan és l'àudio l'afectat, a mi en general m'ha funcionat el separar les pistes d'àudio i de vídeo, i tornar-les a mesclar usant una utilitat de línia d'ordres, però depèn també del format que hagis usat. Si has fet un mpeg 1/2 hi ha el "mplex". Si el teu contenidor és un AVI, hi ha l'"avimerge".

---

### Post by kukat on 2008-09-25
Eps!! Doncs no se m'havia ocurrit fer això que dius de separar l'audio del video...ho provaré aquesta nit (estic a classe i..jejej)

Respecte a l'instal.lació, jo l'instal.le en el "afegir programes", o en la consola, però he vist que en l'script s'instal.len moltes altres llibreries que no estàn a l'instal.lació que ve per defecte a l'Ubuntu (en el meu cas Gutsy Gibbon) i es molt més complicat. Per això vaig pensar que igual estava relacionat amb el mal so que trau....per que feia falta alguna llibreria o alguna cosa "extra"....no se si m'explique.

Gràcies!!!!

---

### Post by kukat on 2008-09-26
He provat els pasos que venen aquí: [https://help.ubuntu.com/community/KdenliveSVN](https://help.ubuntu.com/community/KdenliveSVN), i de moment pareix que va tot bé!!!!
En anar provant ja comentaré alguna cosa!
gràcies!

---

### Post by kukat on 2008-09-29
No funciona bé.....tindrem que esperar a la nova versió. Ara ja ni exporta el projecte ni res..jejejej Alguna alternativa a KDENLIVE??? amb un funcionament paregut, si pot ser (ja he provat el Kino i alguna altre, però com aquest....era el més paregut al Pinnacle..!!)

---

