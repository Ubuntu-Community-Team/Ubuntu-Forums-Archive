---
title: "No puc visualitzar un escriptori remot"
date: 2008-09-22
forum: Catalan Team
---

### Post by lluisalguero on 2008-09-22
Hola,
sovint vaig servir el "visualitzador d'escriptoris remot" per a veure un pc que no tinc al davant però que tinc connectat a la meva xarxa de pc's. Doncs resulta que ara feia uns dies que no el mirava, i quan vull entrar no puc. Aquests son els passos:

[CENTER][[IMG]http://img91.imageshack.us/img91/585/snapshot43kq1.png[/IMG]](http://imageshack.us)[/CENTER]

Vaig a "**Cerca**"

[CENTER][[IMG]http://img65.imageshack.us/img65/7992/snapshot44no8.png[/IMG]](http://imageshack.us)[/CENTER]

i després a "**Domain**", selecciono "AMPLE" (es el nom del domini que vaig ficar per a la meva xarxa)

[CENTER][[IMG]http://img143.imageshack.us/img143/8118/snapshot45eb5.png[/IMG]](http://imageshack.us)[/CENTER]

I quan fico "**D'acord**", aquest és el resultat:

[CENTER][[IMG]http://img65.imageshack.us/img65/8558/snapshot46lz8.png[/IMG]](http://imageshack.us)[/CENTER]

Per a la vostra informació, dir que el pc que "no em deixa veure", va amb el finestres i hi tinc instal·lat el VNC Server.

He estat comprovant que tots dos pc's tinguin les mateixes DNS i que el port 5800 i 5900 estiguin oberts per a aquest pc.

També he estat buscat el significat de NXDOMAIN i el que he trobat em diu això:

> NXDOMAIN quiere decir "INEXISTENT DOMAIN". Quiere decir que estamos haciendo referencia a una máquina o dominio que no existe. .

D'altra banda si vaig a Llocs-> Xarxa, puc veure perfectament els 3 pc's que hi tinc i puc entrar als directoris compartits.

El que no sé si el problema pot vindre de la configuració del meu Ubuntu, o ja és cosa de l'altre que va en finestres.

Només em queda provar si puc entrar des de un pc de fora de la meva xarxa, però justament aquests dies, he canviat de proveïdor d'internet a la linea que tinc a la botiga i per uns dies sembla que estaré sense ADSL.

I abans que m'ho pregunteu, el programari que faig servir en aquell pc, només n'hi ha per al finestres per i per a Mac...o sigui que no tinc alternativa Linux, si el fabricant hagués fet la versió Linux, ja m'hagués passat fa temps.

Si algú vol provar d'entrar remotament, que em pasi un privat i li passaré l'IP...per provar que no quedi.

Una salutació i gràcies,
Lluís

---

### Post by lluisalguero on 2008-09-22
Acabo de fer una prova, des de el pc amb finestres puc entrar via VNC perfectament a l'ubuntu.

Podria ser, llavors, que el problema fos al pc amb finestres? Si fos així, ja no us emprenyaria, ja que com diria el president Pujol: "nois, això ara no toca...cof cof cof "
:lolflag:

---

### Post by lluisalguero on 2008-09-22
Continuo fent proves per descartar coses...he fet algunes modificacions al pc amb finestres i ara ja el puc veure des de el "Client de Terminal Server", però no des de'l "Visualitzador d'escriptoris remots". No entenc com abans ho podia fer, i ara no...

---

### Post by papapep on 2008-09-22
El client de Terminal Server, quan ataca un servidor VNC, fa servir l'Xtightvncviewer, i el visualitzador d'escriptoris remots és el Vinagre, un altre client VNC. Potser sigui un conflicte de versions entre els dos clients i el servidor que tens a l'ordinador que intentes connectar. O un error de configuració, no sé, no tinc més pistes.

En tot cas, amb les "algunes modificacions" que has fet al servidor, que no especifiques, ja has pogut connectar amb l'xtightvncviewer el qual indica que la part de l'Ubuntu funciona correctament, oi?

Respecte que des de l'altre ordinador pots connectar-te a l'Ubuntu, doncs és normal. Ubuntu pot ser un servidor amb tots els ets i uts, l'*altra cosa*, símplement, no :-P

---

### Post by lluisalguero on 2008-09-22
> **papapep said:**
> El client de Terminal Server, quan ataca un servidor VNC, fa servir l'Xtightvncviewer, i el visualitzador d'escriptoris remots és el Vinagre, un altre client VNC. Potser sigui un conflicte de versions entre els dos clients i el servidor que tens a l'ordinador que intentes connectar. O un error de configuració, no sé, no tinc més pistes.

En tot cas, amb les "algunes modificacions" que has fet al servidor, que no especifiques, ja has pogut connectar amb l'xtightvncviewer el qual indica que la part de l'Ubuntu funciona correctament, oi?

Respecte que des de l'altre ordinador pots connectar-te a l'Ubuntu, doncs és normal. Ubuntu pot ser un servidor amb tots els ets i uts, l'*altra cosa*, símplement, no :-P

Les "altres modificacions" han estat simplement, "organitzar" una mica el tallafocs del finestres.

Igual és el que em dius tu que hi ha un conflicte entre el Vinagre i el VNC de l'altre pc, però el que no m'explico és com abans anava i ara de cop i volta no...això és el que em fa ballar el cap

---

