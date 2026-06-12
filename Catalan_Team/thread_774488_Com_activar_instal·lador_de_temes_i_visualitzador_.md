---
title: "Com activar instal·lador de temes i visualitzador de tipus de lletres?"
date: 2008-04-29
forum: Catalan Team
---

### Post by rajoar on 2008-04-29
A dins Sistema / Preferències / Menú principal / Altres, voldria axctivar i poder utilitzar els elements Instal·lador de temes i Visualitzador de tipus de lletres. D'entrada estan desactivats, però encara que els habilito i m'apareixen les icones en el menú Altres, quan vull utilitzar-los no em fan res. És a dir, es queda el punter un ratet rodant fin que desapareix (¿...?). Algú sap que haig de fer per poder utilitzar aquestes utilitats?...

---

### Post by jodufi on 2008-04-29
Hola rajoar,

He provat el que dius amb l'Ubuntu 7.10 i em passa el mateix.

Però aquestes utilitats les pots utilitzar des de «Sistema -> Preferències -> Aparença». 
Allà hi ha la pestanya a «Temes» i la pestanya de «Tipus de lletra»

---

### Post by rajoar on 2008-04-29
Bona nit i gràcies Jodufi,
Sí ja ho he estat utilitzant, però de totes formes crec que no és exactament el mateix..., penso que si responen al redactat del seu enunciat haurien de tenir bastantes més funcions...

---

### Post by oriolsbd on 2008-04-30
Hola, Rajoar.

Em sembla que ja he vist què és. Quan estàs editant les opcions del menú principal, mira les propietats de l'Instal·lador de Temes. Com a ordre, hi posa:
gnome-appearance-properties -i %u

El text " -i %u" em sembla que intenta instal·lar un tema que se li hauria de passar per paràmetres. Modifica aquesta ordre per, simplement:
gnome-appearance-properties

I a mi ja se'm veu correctament.

Quant al visualitzador de lletres, també hi té un paràmetre (la font de lletra a visualitzar), però si se li treu el paràmetre, tampoc no s'obre res (no es pot executar sense paràmetres). Sembla que aquest programa s'ha d'invocar des de terminal. Jo, per exemple, he fet des de terminal:
gnome-font-viewer /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf

I m'ha mostrat la font DejaVuSans, però tampoc no me'n deixa obrir una altra. No sé si és aquest el programa que realment vols.

Salut!

---

