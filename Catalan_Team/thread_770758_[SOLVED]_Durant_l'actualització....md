---
title: "[SOLVED] Durant l'actualització..."
date: 2008-04-27
forum: Catalan Team
---

### Post by Joan Marc on 2008-04-27
Hola,
Estic actualitzant a Hardy Heron 8.04.
Instal·lant els paquets, em surt la pantalla adjunta, què he d'escollir?

Gràcies :)

---

### Post by Joan Marc on 2008-04-27
He clicat al botó Ajuda, i em diu això:
```
Hi ha una nova versió del fitxer /boot/grub/menu.lst, però la vostra versió s'ha modificat localment
```

Després he provat "Show the differences betwen the versions" i em surt el següent
```
--- /var/run/grub/menu.lst 2008-04-27 18:32:05.769012151 +0200
+++ /tmp/file2rHpIg 2008-04-27 18:32:05.000000000 +0200
@@ -2,18 +2,10 @@
 
 title Ubuntu 7.10, kernel 2.6.22-14-generic
 root (hd0,3)
-kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro locale=ca_ES
+kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro quiet splash locale=ca_ES
 initrd /boot/initrd.img-2.6.22-14-generic
 quiet
 
-# This entry automatically added by the Debian installer for a non-linux OS
-# on /dev/sda2
-title Microsoft Windows XP Professional
-root (hd0,1)
-savedefault
-makeactive
-chainloader +1
-
 title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
 root (hd0,3)
 kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro single
```

I en canvi, el meu menu.lst actual (de Gutsy Gibbon) és:
```
## ## End Default Options ## ## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,3) root (hd0,3)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=917 | kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=917
initrd /boot/initrd.img-2.6.22-14-generic initrd /boot/initrd.img-2.6.22-14-generic
quiet quiet

# This entry automatically added by the Debian installer for <
# on /dev/sda2 <
title Microsoft Windows XP Professional <
root (hd0,1) <
savedefault <
makeactive <
chainloader +1 <
 <
title Ubuntu 7.10, kernel 2.6.22-14-generic (recove title Ubuntu 7.10, kernel 2.6.22-14-generic (recove
root (hd0,3) root (hd0,3)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=917 kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=917
initrd /boot/initrd.img-2.6.22-14-generic initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+ title Ubuntu 7.10, memtest86+
root (hd0,3) root (hd0,3)
kernel /boot/memtest86+.bin kernel /boot/memtest86+.bin
quiet quiet

### END DEBIAN AUTOMAGIC KERNELS LIST ### END DEBIAN AUTOMAGIC KERNELS LIST
```

He vist, que en el primer, no hi ha l'entrada del memtest... que no la te la Hardy Heron?

---

### Post by Joan Marc on 2008-04-27
Weno... cap comentari...xD
He tirat pel dret, i m'he trobat amb el següent:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro quiet splash locale=ca_ES
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro quiet splash locale=ca_ES
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=917bd13d-9ec9-4ed9-ba3f-0bbd85546937 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
```

Però ni rastre de la partició de Windows... que faig?

---

### Post by Joan Marc on 2008-04-27
Ja he posat l'entrada del Windows, que he agafat d'una copia de segureat que tenia.
El que trobo estrany és que hi hagi 5 entrades d'Ubuntu Hardy Heron, en puc eliminar cap? quina?

Gracies

---

### Post by uidb4056 on 2008-04-27
Si arrancant amb le opcio que posa la versio 2.6.24-16 et va be, pots eliminar les entrades que posa 2.6.24-14.

---

### Post by Joan Marc on 2008-04-27
Merci per contestar.
Perquè hi ha més d'una versió?

---

### Post by uidb4056 on 2008-04-27
Perque se t'ha actualitzat el kernel i et mante l'opcio antiga, Aixó va be perque si tens problemes pots arrancar amb el kernel anterior. Si el kernel nou et va bé pots esborrar-ho.

---

### Post by Joan Marc on 2008-04-27
OK merci... però em sembla, que per un cas, no l'esborraré, sinó que li posare # al davant!

Gracies

---

### Post by CarlesOriol on 2008-04-28
No, fent això sols elimines que es vegi al grub.

Has d'eliminar l'entrada amb el synaptic i s'eliminaran un munt de megues per cada nucli així com la opció al grub.

---

### Post by Joan Marc on 2008-04-28
Com ho he de buscar al Synaptic? Amb Ubuntu o Kernel o alguna cosa per l'estil? (Ara no estic amb un ubuntu i no ho puc mirar xD)

Gràcies

---

### Post by CarlesOriol on 2008-04-28
linux-image-.... 

Vigila de no carregar-te la bona... o no li agradarà gens al teu ordinador i al reiniciar patiras una pena molt gran.

---

### Post by Joan Marc on 2008-04-28
Ja ho he fet, gracies.

PD: Com carai es fa per posar Solved? a Thread tools no hi és :S

---

### Post by SiscoGarcia on 2008-04-28
> **Joan Marc said:**
> Ja ho he fet, gracies.

PD: Com carai es fa per posar Solved? a Thread tools no hi és :S

Pel que fa a les noves "possibilitats" del fòrum, hi ha tot un [fil que en parla]("http://ubuntuforums.org/showthread.php?t=762416")...

... i encara no n'hem tret l'aigua clara. Però sembla ser que és temporal i més endavant hi haurà més opcions.

---

### Post by Joan Marc on 2008-04-28
Merci, ja ho he preguntat alla.

---

### Post by SiscoGarcia on 2008-04-28
Ja ho he vist i he dit el que penso (podem modificar el títol del fil posant al davant "SOLVED" sense cometes). ;)

---

