---
title: "ManDVD problema permís escriptura"
date: 2008-05-17
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-05-17
Bones.
En intentar grabar o editar un vídeo amb ManDVD, hem surt un missatge que diu: "No se puede crear el archivo. ¿Tiene permiso escritura en carpeta destino?"
Per asegurar els drets d'escriptura a la carpeta vídeos, des de terminal he fet: "sudo chmod -R 777 Vídeos", però no ha servit de res.

També he obert al nautilus com ha root, terminal "sudo nautilus".
A la carpeta "Vídeos", propietats, permisos; on diu "Accés al fitxer" hem surten 3 ratlles "---". Si ho canvi-ho a "Lectura/Escriptura", en tancar la finestra i obrir-le de nou, tornen a sortir les 3 ratlletes.

Crec que tinc un probleme de permisos?

Hem podeu ajudar?
Gracies.

---

### Post by papapep on 2008-05-17
El primer que hauries de fer és verificar quins permisos té aquesta carpeta ara:

```
ls -la /elcamícomplertfins/Vídeos/
```

---

### Post by Miquel Ubuntero on 2008-05-17
Mestre!
Aquí te el que hem demana ;)

miquel@miquel-desktop:~$ ls -la /home/miquel/Vídeos
total 166136
drwxrwxrwx  3 miquel miquel      4096 2008-05-17 00:02 .
drwxr-xr-x 51 miquel miquel      4096 2008-05-17 18:54 ..
drwxrwxrwx  3 miquel miquel      4096 2008-05-17 15:31 Cantabria
-rwxrwxrwx  1 miquel miquel  27170075 2008-04-11 23:26 thriller
-rwxrwxrwx  1 miquel miquel 142754024 2008-04-16 20:04 thriller.mpg
miquel@miquel-desktop:~$ 

Salut!

---

### Post by papapep on 2008-05-17
mmmm.....i aquest directori /Vídeos és dins el disc "normal" de l'ordinador?

Enganxa el que mostri un:

```
cat /etc/mtab
```

Per cert, aquest ManDVD jo no el conec gens, o sigui que seria bo que fessis un bon cop d'ull a l'apartat on es defineix on desar els vídeos, no sigui que hi hagi algun paràmetre que t'estigui fent la punyeta.

---

### Post by Miquel Ubuntero on 2008-05-17
Hola Papapep.
Aquí ho tens:
miquel@miquel-desktop:~$ cat /etc/mtab
/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
miquel@miquel-desktop:~$ 

Moltes gracies pel teu interés.
Salut!

---

### Post by papapep on 2008-05-18
Pel que veig a l'mtab, no tens un disc dur extern, sinó un únic disc dur intern...

Aquí tens els permisos bé, o sigui que no té massa sentit:

> drwxr**[COLOR="Red"]-[/COLOR]**xr[COLOR="Red"]**-**[/COLOR]x 51 miquel miquel 4096 2008-05-17 18:54 ..

---

### Post by Miquel Ubuntero on 2008-05-18
hola de nou.
Tal com papapep comenta, el tema no està gaire clar.
referent a la carpeta on ManDVD desa les feines, l'he canviat a diferents carpetes i res.
Avui he reinstal·lat ManDVD i tampoc ha servit de res. Ho he fet fent doble clic al arxiu extensió .deb i fent clic a el botó "Reinstal·la el paquet".
Si tinc temps, eliminaré i reinstal·laré totes les dependencies (que en son unes quantes!)
ja us comentaré.
Salut!

---

