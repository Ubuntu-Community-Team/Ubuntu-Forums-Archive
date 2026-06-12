---
title: "[SOLVED] Linux Image Error 2"
date: 2008-02-12
forum: Catalan Team
---

### Post by kukat on 2008-02-12
E: linux-image-2.6.22-14-generic: el subprocés post-installation script retornà el codi d'eixida d'error 2
E: linux-image-2.6.22-14-rt: el subprocés post-installation script retornà el codi d'eixida d'error 2

Hem surt el següent missatge a l'hora d'instal.lar qualsevol aplilcació????:confused:

**En la consola hem surt açò:**

S'està configurant linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.22-14-generic (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 2
S'està configurant linux-image-2.6.22-14-rt (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.22-14-rt (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 linux-image-2.6.22-14-generic
 linux-image-2.6.22-14-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)
[B]
Crec que la primera vegada que hem va passar va ser quan vaig intentar instal.lar unes actualitzacions...[/B]

Alguna suggerència?  Gràcies!

---

### Post by papapep on 2008-02-12
Ostres, ostres....prova amb un:

```
sudo dpkg --configure --pending
```

a veure si t'acaba el procés que sembla que, en algun moment, s'ha quedat "atontat".

---

### Post by papapep on 2008-02-12
Oblida el que t'he dit abans. Prova a rectificar el fitxer /sbin/update-grub de la següent manera (fes còpia de seguretat abans!!!):

```
sudo cp /sbin/update-grub /sbin/update-grub.backup
```

```
sudo nano /sbin/update-grub
```

i a la primera línia, on diu:

```
#!/bin/sh
```

fes que quedi:

```
#!/bin/bash
```

Desa (Ctrl + X) i prova a fer un:

```
sudo apt-get -f install
```

---

### Post by patrickfromspain on 2008-02-12
ostia! el mateix que té la meva novia!!! De moment, provant coses, he deixat el sistema bastant tocat.. a vere si puc provar el que ha dit en papapep, perque la cosa semblava tenir molt mala solució.

salut!

---

### Post by papapep on 2008-02-12
> ostia! el mateix que té la meva novia!!!

....quines novies més curioses que et busques, que les hi has d'actualitzar el kernel ;)

---

### Post by kukat on 2008-02-12
crec que ha eixit bé! ara vaig a reiniciar. Espere tornar a editar el missatje:) jejejej
Gràcies

edito: Ha funcionat! ja està instalant les actualitzacions correctament! jejejejejeje. Moltíssimes gràcies! Crec que va millor l'ordinador en tots els aspectes. Es veu que s'havia quedat tonto de veritat.

---

### Post by patrickfromspain on 2008-02-17
Pujo aquest missatge per donar les gracies al Papapep... al final ho vaig poder arreglar començant amb el que havies posat. :)

Despres em va tocar barallar-me per restaura la configuracio grafica.. pero ja es una altra historia x-D

salut!

---

