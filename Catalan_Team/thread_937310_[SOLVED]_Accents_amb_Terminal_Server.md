---
title: "[SOLVED] Accents amb Terminal Server"
date: 2008-10-03
forum: Catalan Team
---

### Post by Carles_BE on 2008-10-03
Una consulta a veure si algú s'hi ha trobat anteriorment

Faig anar un ordinador amb Ubuntu 8.04 i utilitzo Terminal Server per a connectar amb un ordinador remot que funciona amb Windows Xp ... 

Em trobo amb el problema que no puc escriure accents quan accedeixo d'aquesta forma a l'ordinador remot

Fa la sensació com si, en accedir remotament, el teclat funcionés amb anglès ... 

El cas és que el teclat està correctament configurat tant a l'ordinador amb Ubuntu com a l'ordinador remot ...

He consultat a la web i hi ha molta informació sobre problemes amb accents però, pel que he vist, són problemes amb VirtualBox o amb teclats anglesos ... no exactament el que em passa a mi

Algú s'hi ha trobat amb això?

Gràcies

---

### Post by lukjad on 2008-10-03
Ho sento si estic parlant malament, estic anglès.

Pot ser el protocol que està utilitzant. Pot ser configurat erròniament. A més, està utilitzant un teclat català en ambdós equips? Si no és així, llavors potser és que el teclat és simple enviament de senyals (vocals) que el sistema operatiu dels canvis que els accents. Si aquest és el cas, llavors potser en l'intercanvi entre els equips hi ha un mixup. Tracti d'obtenir el mateix tipus de teclat en ambdós (si és possible) i veure si el problema continua.

Ho sento de nou, si estic parlant malament.

Sorry if I am speaking incorrectly, I am English.

It may be the protocol you are using. It could be misconfigured. Also, are you using a Catalan keyboard on both computers? If not, then may be it is that the keyboard is sending simple characters that the Operating System changes to have accents. If that is the case, then maybe in the exchange between the computers there is a mixup. Try getting the same type of keyboard on both (if possible) and see if the problem continues.

Sorry again if I am speaking badly.

---

### Post by CarlesOriol on 2008-10-04
No t'ha de passar:

comprova que al client en ubuntu tries el mapa de teclat es. (a Recursos locals).
Si uses directament el rdesktop fas: rdesktop ip -k es

Un cop dins del güindous comprova que la màquina té el teclat es seleccionat. (sobretot si es un servidor en angles o similar)

---

### Post by Carles_BE on 2008-10-07
Bé, ja ho he solucionat ... la cosa és tonta ... 

resulta que, quan accedeixo a la màquina remota (que funciona amb Windows) per defecte es fica en llenguatge EN(glish) ... encara que normalment estigui amb CA(talà)

això es veu mitjançant un petit requadre blau amb caràcters blancs que es troba a la part de sota a la dreta de la pantalla (al costat del rellotge) ... passa que en moltes ocasions aquest requadre roman ocult (o fins i tot no es visualitza) ... m'he adonat d'això investigant sobre el rdesktop (que em suggeríeu en un post anterior)

En fi, que s'ha d'accedir a Windows i anar directament a canviar EN(glish) per CA(talà) ... només cal clicar a sobre del requadret esmentat i ficar el mode de teclat que es vulgui

Gràcies a tots per la vostra ajuda ... això del Windows sempre és problemàtic ...

---

