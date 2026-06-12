---
title: "[SOLVED] Desapareix icona internet"
date: 2008-05-10
forum: Catalan Team
---

### Post by lFossil on 2008-05-10
Hola a tots!
Ja fa temps que no sé per què em va desaparèixer la icona que surt per defecte de l'internet en el quadre superior a la dreta en el gutsy gibbon.
L'única solució que hi vaig trobar va ser instal·lar el Wifi-radar, però m'agradaria tenir el d'abans per què hi han cops que aquest no em funciona bé.

He buscat en les aplicacions disponibles al anar a "Afegeix al quadre" a veure si estava allí, però no hi és.

---

### Post by lo gambusí on 2008-05-10
Millor fes una captura o explica't millor, perquè jo com a mínim no t'hai entès massa.:?

---

### Post by RainCT on 2008-05-10
Ves a Sistema -> Preferències  -> Sessions (pestanya: Programes d'inici) i comprova que hi surti una entrada anomenada "Network Manager" i que aquesta estigui marcada. Hi ha 3 possibilitats:

[LIST]
[*] Que ja estigui marcada: Els trets no van per aquí. Obre una terminal, executa-hi «nm-applet --sm-disable» i enganxa'ns el que et digui (si és que diu alguna cosa).
[*] Que no estigui marcada: Marca-la, tanca i tornar a obrir la sessió (o si no vols haver de tornar a entrar fes Alt + F2 i executa «nm-applet --sm-disable») i ja t'hauria de tornar a funcionar.
[*] Que directament no surti: en aquest cas, fes clic en "Afegeix" i al diàleg que et surt posa a Nom «Network Manager» i a Ordre «nm-applet --sm-disable». Llavors segueix les instruccions del punt anterior i ja està.
[/LIST]

Espero que et serveixi.

---

### Post by lFossil on 2008-05-11
Surt marcat, llavors he ficat el  que m'has dit al terminal, però no m'ha sortit res.:confused:

---

### Post by lFossil on 2008-05-12
Alguna idea?
Si algu no m'ha entès, el que dic és que m'ha desaparegut l'icona per triar les xarxes sense fil o amb fil disponibles.

---

### Post by RainCT on 2008-05-13
Suposo que les icones dels altres programes que haurien de sortir a la barra (Pidgin, etc.) si que et surten, no?

Perquè si no hi són, el problema és que has esborrat l'àrea de notificació. La solució a això seria fer clic dret al panell, triar «Afegeix al quadre...» i la finestra que surt fer doble clic sobre «Àrea de notificació» per tornar-la a afegir al panell.

---

### Post by CarlesOriol on 2008-05-13
El tema d'icones a Sistema->preferencies->aparença pot ser que no tingui icona per aquesta acció del nm-applet.

---

### Post by lFossil on 2008-05-13
No trobo això de l'àrea de notificació:confused:

---

### Post by RainCT on 2008-05-13
Com que no? Explica't! :P

[img]http://img505.imageshack.us/img505/9849/afegirareanotificaciots0.png[/img]

---

### Post by lFossil on 2008-05-13
Ok d'acord ja està. No ho trobava.:)
Moltes gràcies!!

---

