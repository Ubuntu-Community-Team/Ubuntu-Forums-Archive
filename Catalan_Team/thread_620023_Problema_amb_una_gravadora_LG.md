---
title: "Problema amb una gravadora LG"
date: 2007-11-22
forum: Catalan Team
---

### Post by lluis.dalmau on 2007-11-22
Des de que he actualitzat a la gusty la gravadora que tinc al pc fa el ruc.

El led del frontal de la gravadora es va encenent i apagant, fa algun soroll d'activitat però no hi ha cap disc, al prémer el botó no s'obre i tampoc es pot muntar/desmuntar/expulsar.

Alguna idea del què pot estar passant ?

---

### Post by nickpage on 2007-11-22
Això es semblant al que m'ha passat amb el meu disc dur extraible...

---

### Post by torracastanyes on 2007-11-24
Hola Lluis.
No et puc ajudar gaire, perquè no sé la solució, però també m'ha passat.
Quan vaig instal.lar Feisty en un Acer power nou, amb una grabadora LG GSA-H11N, em feia el mateix, a més em sortía un avís dient que tenía un cd d'audio  dintre.
Vaig probar varies coses, però no m'en vaig sortir. Al final, vaig canviar-la per una que tenía en un pc vell i va funcionar.  
La LG que feia el ruc la vaig montar en el mateix pc vell i funciona perfecta, així que penso que podía ser un comflicte entre dispositius, però jo no sé on buscar-lo.
També ho vaig preguntar a Ubuntu.es, però ningú va contestar.

Edito: He repassat el post que vaig escriure llavors i m'ha recordat un detall que m'ha passat per alt:
Quant vaig fer la instal.lació de Feisty, vaig emprar una beta, perquè la estable encara no había sortit, i la grabadora va funcionar bé fins que la vaig actualitzar.

---

### Post by lluis.dalmau on 2008-01-16
Sembla que hi ha un bug:
[https://bugs.launchpad.net/linux/+bug/75295/comments/95](https://bugs.launchpad.net/linux/+bug/75295/comments/95)

Hi havia moments que 'udevd' es menjava tot el processador i memòria.

Fet el què diu l'enllaç anterior ha deixat de fer soroll, encendre el led, menjar-se els recursos i, finalment, funciona la gravadora ;)

---

