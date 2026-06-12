---
title: "[SOLVED] Canviar nom particions"
date: 2008-10-25
forum: Catalan Team
---

### Post by jaume69 on 2008-10-25
Com es fa per canviar el nom de les particions,quan les munto a l'escriptori.

Vull dir,que en ves que surti,"**Soporte de 50GiB**",em surti **-Windows Vista de xxGiB**-,-**Kubuntu 8.04 de xx**GiB-,etc...

O no es pot fer?

Si hi ha molt de "cacau",ja m'està bé com està..

[-o<

---

### Post by PatrickVogeli on 2008-10-26
per les particions ext2 o ext3: sudo e2label /dev/sdX NOM. Per les particions ntfs: instal·la el paquet ntfsprogs i despres sudo ntfslabel /dev/sdY NOM.

salut

---

### Post by jaume69 on 2008-10-26
Doncs ja ho he fet i ja funciona.

Pero en el **Nom** si poso **Windows Vista** no ho acepta i **Windows-Vista**,si.

O Kubuntu-8.04.(casi no la faig servir)(Tampoc Windows)

I s'ha de Reiniciar,que no ho sabia.

Gràcies!.

---

### Post by PatrickVogeli on 2008-10-26
has provat sudo ntfslabel /dev/sdY Windows\ Vista ?

---

### Post by jaume69 on 2008-10-26
Doncs si,ara està perfecte.
Merci.

---

