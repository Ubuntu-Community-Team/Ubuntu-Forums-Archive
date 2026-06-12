---
title: "Problemes amb l'UCK"
date: 2008-04-24
forum: Catalan Team
---

### Post by SiscoGarcia on 2008-04-24
Hola,

Acabo de baixar-me la versió estable de la Hardy i he intentat catalanitzar-la amb l'UCK (Ubuntu Customization Kit). Aquest programa ja l'he fet anar amb èxit un altre cop, però ara no me'n surto. Trio les opcions de català i després dic que no vull muntar res jo a mà i que no vull desfer-me'n dels win32, i em diu que no pot muntar-lo (acompanyo captura del missatge) i que revisi el build.log que adjunto:

> Starting CD remastering on  dj abr 24 18:45:23 CEST 2008
Customization dir=/home/sisco/tmp/customization-scripts
Removing ISO remastering dir...
Mounting ISO image...
Unpacking ISO image...
Unmounting ISO image...
Mounting SquashFS image...
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Cannot mount /home/sisco/tmp/remaster-iso/casper/filesystem.squashfs in /home/sisco/tmp/squashfs-mount, error=32
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
DCOP Cleaning up dead connections.
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ICE default IO error handler doing an exit(), pid = 7350, errno = 0

Jo no sé veure-hi res. Algú pot ajudar?

Gràcies.

---

### Post by papapep on 2008-04-24
Extret d'aquí:
[https://bugs.launchpad.net/uck/+bug/215697](https://bugs.launchpad.net/uck/+bug/215697)

> as i told you by mail, you can remaster an 8.04 only within an 8.04, that's depending on kernel modules version and we can't solve that in any way

O sigui, que només pots fer anar l'UCK per fer una imatge de Hardy, des de dins una Hardy mateix...ho sento.

---

### Post by SiscoGarcia on 2008-04-24
Acabo de veure una notícia semblant a la llista. Doncs m'hauré d'actualitzar a la 8.04 per poder fer la versió catalanitzada. Per cert, algú del LoCo la fa pel dissabte, no?

---

### Post by jmaspons on 2008-04-25
Hola Sisco,
A [Caliu ]("http://caliu.cat/blog/2008/04/24/la-kubuntu-804-hardy-en-catala-al-servidor-de-caliu/") ja l'han penjat. De moment només hi ha kubuntu però, perquè volem més? :P

Com a molt hi trobaria a faltar la versió amb KDE4...    :lolflag:

---

### Post by orestesmas on 2008-04-25
> **jmaspons said:**
> Com a molt hi trobaria a faltar la versió amb KDE4...    :lolflag:

Si vols la faig...

Orestes.

---

