---
title: "Error 15 del grub"
date: 2008-07-09
forum: Catalan Team
---

### Post by LitusMayol on 2008-07-09
Bones,

fa un temps vaig tenir un error al carregar el grub. Quan intentava carregar una de les particions on tenia **Ubuntu**em sortia això:

```
Error 15: File not found
```. 

L'error ja el vaig postejar en [aquest]("http://ubuntuforums.org/showthread.php?t=837439&page=2") post. 


Doncs ja ho he soluciona. Simplement he comparat el *menu.lst* que carregava ara amb el que carregava abans i resulta que el grub que tenia jo ara no tenia l'últim Kernel. Vull dir, que l'**Ubuntu** que utilitzo és "vmlinuz-2.6.24-18-generic" i jo l'últim que tenia al grub era el "vmlinuz-2.6.24-16-generic". 

Per arreglar-ho vaig haver de afegir el "vmlinuz-2.6.24-18-generic" al *menu.lst*.

```
gksu gedit /boot/grub/menu.lst
```


Per si algú li serveix. Aquest post no té cap problema, té una solució per si algú es troba amb aquest problema.

---

### Post by papapep on 2008-07-09
> Per si algú li serveix. Aquest post no té cap problema, té una solució per si algú es troba amb aquest problema.

Doncs marca'l com a solucionat, Litus.

---

