---
title: "[SOLVED] Fer conviure Ubuntu y Fedora"
date: 2008-10-25
forum: Catalan Team
---

### Post by Daerun on 2008-10-25
Hola a tots, m'acabo d'instal·lar Fedora 9  en una partició nova per veure com funciona, però un cop fet, resulta que el grub (o el que sigui) del fedora es "menja" el que tenia fins ara, y com a resultat, l'Ubuntu no apareix com a opció. Ho he arreglat amb un CD amb el SuperGrub, restaurant el grub com el tenia abans, y ara el que no m'apareix és el fedora. el que voldria fer és que m'apareguin tots els SO (el güindows encara el tinc per aqui, encara que no el faig servir mai :mrgreen: ), com ho puc fer això?

---

### Post by Daerun on 2008-11-05
Al final ho vaig arreglar una mica escadusserament, perquè no he trobat com fer que el grub s'actualitzi automáticament.

La cosa és anar a la partició Fedora, a l'arxiu /boot/grub/menu.lst y copiar-hi les línies corresponents a l'arrencada d'aquella distro; després anar al mateix arxiu del nostre Ubuntu, y enganxar-les perquè apareguin a l'arrencada del grub. En cas de que s'actalitzi el kernel del Fedora, cal repetir-ho un altre vegada manualment, per això dic que és una mica escadusser, però en fi, funciona.

Recomano a qui vulgui instal·lar-se una altra distro que abans es descarregui el CD del SuperGrub, per si de cas passa el mateix que a mi. S'arrenca el PC amb aquest, i un cop seleccionat l'idioma (està en català), es selecciona la opció GNU/LINUX, després > Arregla Arrencada de GNU/LINUX (GRUB), aqui apareixeran les dues opcions possibles (en el meu cas, Fedora y Ubuntu), selecciones una, pitjes Enter, y ja está, el que hagis seleccionat es converteix en el predeterminat amb el que s'arrencarà.

EDITO per enganxar aqui la línea (o línies) que caldria enganxar al nostre /boot/grub/menu.lst per si algu no ha remenat mai aquestes coses que no s'equivoqui.

title Fedora     (2.6.26.6-79.fc9.i686)
root         (hd0,2)
kernel         /boot/vmlinuz-2.6.26.6-79.fc9.i686 ro root=UUID=23ed508f-9cb5-4201-93ed-8498b078b66d rhgb quiet
initrd         /boot/initrd-2.6.26.6-79.fc9.i686.img


title         Fedora (2.6.25-14.fc9.i686)
root         (hd0,2)
kernel         /boot/vmlinuz-2.6.25-14.fc9.i686 ro root=UUID=23ed508f-9cb5-4201-93ed-8498b078b66d rhgb quiet
initrd         /boot/initrd-2.6.25-14.fc9.i686.img

---

