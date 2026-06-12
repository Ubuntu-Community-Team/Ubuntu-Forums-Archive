---
title: "[SOLVED] Modificar el Grub"
date: 2008-03-04
forum: Catalan Team
---

### Post by Joan Marc on 2008-03-04
Hoa a tots,
Tinc un petit dubte sobre el grub.
El cas és que tinc com a primera entrada el WinXP, i voldria posar l'ubuntu.
El que no sé, és quines línies he de copiar perquè funcioni. Us poso l'apartat del menu.lst que es diu ## ## End Default Options ##

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro locale=ca_ES
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
```

Em prdrieu dir què he de moure exactament?
Moltes gràcies

PD: Ja sé que és molt bàsic, però tinc por de que no arranqui bé x)

---

### Post by SiscoGarcia on 2008-03-04
Hola Joan Marc. Jo el que faria és retallar el tros que correspon al windows

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

i enganxar-lo després del que ens has passat (la del memtest d'ubuntu). D'aquesta manera la primera opció per engegar serà l'ubuntu.

Una altra opció seria enlloc de retallar-lo, copiar-lo; enganxar-lo on t'he dit i després afegeixes # al davant de cada línia de la part de windows perquè no t'aparegui i així te n'assegures que no ho perds.

---

### Post by Joan Marc on 2008-03-04
D'acord... però això:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

Ho he de retallar juntament amb el WinXP o deixar-ho on està?

---

### Post by papapep on 2008-03-04
[COLOR="Red"]**ABANS**[/COLOR] de fer res de res, recorda fer-ne una còpia de seguretat:

```
sudo cp /boot/grub/menu.lst boot/grub/menu.lst.backup
```

Les línies que esmentes són comentaris, pots fer-ne el que vulguis. Tot i que, per claredat, estaria bé que anessin amb les altres que mous del Hasefroch.

---

### Post by Joan Marc on 2008-03-04
Gràcies als dos. Tot correcte :)

---

