---
title: "[SOLVED] Botons de finestra a l'inravés"
date: 2008-09-29
forum: Catalan Team
---

### Post by tanreb20 on 2008-09-29
Hola!!!!

Des que em vaig decidir a esborrar el compiz, l'emerald i totes aquestes mandanges, em pasa una cosa cuiriosa.

Els botons de finestra apareixen, pero a la banda esquerra en ordre invers(tancar - maximitzar - minimitzar), aixo em apssava ja amb el compiz quan el desahbilitava. com els puc tornar a posar normal?

També em passa que la majoria de temas d'icones que tinc instalats no funcionen i e sveuen icones d carpeta i tal que no funcionen

---

### Post by jaume69 on 2008-09-30
[QUOTE="tanreb20"]Els botons de finestra apareixen, pero a la banda esquerra en ordre invers(tancar - maximitzar - minimitzar), aixo em apssava ja amb el compiz quan el desahbilitava. com els puc tornar a posar normal?[/QUOTE]

Que no sigui que no has canviat el tema Gtk,des de Sistema-Preferencies-Apariencia.

[QUOTE="tanreb20"]També em passa que la majoria de temas d'icones que tinc instalats no funcionen i e sveuen icones d carpeta i tal que no funcionen[/QUOTE]

Hi ha vegades que no s'instal.len bé alguns paquets d'Icones a **Gnome-look**,no sé perquè.


No sé si aquest és el teu problema o bé algun conflicte de paquets amb Compiz.  :confused:

---

### Post by patrickfromspain on 2008-10-01
L'ordre de les icones, mira al gconf-editor sota apps -> metacity -> general -> button_layout, a veure si es això. Jo els tinc normals, i ho tinc com a "menu:minimize,maximize,close" (sense cometes).

Els temes d'icones: amb el gnome 2.20 es van canviar moltes coses i els temes fets per a gnomes anteriors no van bé, s'han d'actualitzar els nomes de les icones.

salut

---

### Post by tanreb20 on 2008-10-02
Perfecte!!

Solucionat!

---

