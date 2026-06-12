---
title: "[SOLVED] sense acces hda1"
date: 2008-03-14
forum: Catalan Team
---

### Post by pserra on 2008-03-14
[SIZE="4"]Hola companys, ja se que potser es una pregunta molt bàsica.. però porto estona liat amb muntar la hda1 que  no se que li ha pasat que no hi puc accedir des de Ubuntu.
Agrairia ajuda
miro com tinc els permisos, des de root desmunto hda1, i com a usuari normal 
el munto... pero alguna cosa he fet malament o no la veig...

Consola:[/SIZE]

pere@Ubuntu:~$  ls -l /media
total 36
lrwxrwxrwx 1 root root     6 2007-03-15 19:49 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2007-03-15 19:49 cdrom0
lrwxrwxrwx 1 root root     7 2007-03-15 19:49 floppy -> floppy0
drwxrwxr-x 2 pere pere  4096 2007-03-15 19:49 floppy0
drwxrwxr-x 2 pere pere  4096 2007-04-08 00:22 floppy-1
drwxrwxrwx 1 root root  8192 2008-03-12 00:22 hda1
drwxrwxrwx 8 root root 16384 1970-01-01 01:00 hda5
pere@Ubuntu:~$  sudo umount /media/hda1
pere@Ubuntu:~$ mount /media/hda1
mount: només l'usuari root pot muntar /dev/sda1 a /media/hda1
pere@Ubuntu:~$

Cordialment...

---

### Post by CarlesOriol on 2008-03-15
sudo mount /dev/sda1 /media/hda1

Ah... si us plau respecta la mida de text del fòrum.

---

### Post by pserra on 2008-03-15
Merci,
 solucionat  ara ja el puc carregar i disculpes per la mida.
Cordialment..

---

### Post by jodufi on 2008-03-15
Doncs ara pots marcar el fil com a «Solved» i donar-lo per tancat :)

---

### Post by pserra on 2008-03-16
disculpa judofi, 
com es fa de donar un fil per tancat(solved)??
Cordialment...

---

### Post by menut on 2008-03-16
Thread tools (on hi ha una fletxeta cap avall) > Mark this thread as solved.

---

