---
title: "Modificar Resolució de la Finestra d'Entrada"
date: 2008-10-31
forum: Catalan Team
---

### Post by kukat on 2008-10-31
Hi ha alguna forma de modificar la resolució de la finestra d'Entrada?
El meu monitor no suporta aquesta resolució i m'ix "Out of Range". De moment, he llevat la Finestra d'Entrada i he posat l'entrada automàtica!O:)

---

### Post by papapep on 2008-10-31
Afegeix el que vulguis d'aquests modes a la línia d'arrencada del nucli (només el "vga=XXX", clar):

vga=785 --> 640x480

vga=788 --> 800x600

vga=791 --> 1024x768

vga=794 --> 1280x1024

---

### Post by CarlesOriol on 2008-11-01
Parlem de l'entrada del logo d'ubuntu (com ha dit en papapep) o de l'altra on s'escriu el mot de pas? (gdm)

---

### Post by kukat on 2008-11-01
es l'entrada on es posa l'usuari i la contrasenya. No se molt bé per què, però supose que estarà amb una resolució molt alta, ja que m'ix el "Out of Range". 
Bon dia de Tots Sants!

---

### Post by jaavier on 2008-12-19
Hola!
Tinc un amic que té el mateix problema que tu amb el "out of range" i crec que gracies a tu li podré solucionar... A veure, a mi em va passar una altre cosa pero la modificació seria la mateixa...
Afegint això al teu xorg.conf:
```
Section "Screen"
    Subsection "Display"
        [...]
        Virtual 1280 1024
        [...]
    EndSubsection
EndSection
```
On "1280 1024" correspon a la teva resolució (igual! així sense x al mig i sense cometes)
Crec que et funcionará, perqué jo utilitzo la pantalla del portatil i una altra externa i em quedaba la el kdm (utilizo Kubuntu xD) tallat a la meitat de les dues pantalles, i amb això aconsegueixo que al kdm s'engegui només la pantalla del portatil (restringint la resolució del kdm).
NOTA: Jo tinc Nvidia, pero en teoria això ara no hauria d'afectar.

---

