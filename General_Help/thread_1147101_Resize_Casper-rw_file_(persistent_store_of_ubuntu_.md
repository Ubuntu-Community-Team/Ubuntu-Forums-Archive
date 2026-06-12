---
title: "Resize Casper-rw file (persistent store of ubuntu on usb pendrive)?"
date: 2009-05-03
forum: General Help
---

### Post by DanyX on 2009-05-03
Hi,

I created a bootable ubuntu 9.04 install on a 2gb usb stick with the ubuntu live cd. I already configured quite a bit of stuff, and I would like to try a few more packages now. The problem is, I am running out of space - I created the persistence file to be 500mb because I wanted some space left on my usb stick, but now I would like to enlarge this. Is that possible? Can I resize the casper-rw file (I think that's the one that would need resizing)?

Thanks for your help in advance!
Daniel

---

### Post by dandnsmith on 2009-05-03
I don't know how you resize it, but do know how to create a new one and copy the content from the old to the new. It's based on stuff in pendrivelinux.com

first make the basis for a new casper-rw

dd if=/dev/zero of=*your new filename* bs=1M count=*number of blocks*

then make the filesystem on it

mkfs.ext3 -F *your new filename*

now do the copy after mounting the old and new files
create 2 new mount points

mount -o loop oldfile /mnt/mountold
mount -o loop newfile /mnt/mountnew


now do the copy using 

cp -a  

to get permissions etc correct.

Now you can replace the old casper-rw with the new, and away you go

---

### Post by geirha on 2009-05-03
You can also resize the filesystem. First, you need to extend the image file to the desired size. If you want increase the size from 500MB to 1GB, you'll need to add 500MB of zeroes to the end of the file.

It's a good idea to backup the image first.

1. add 500MB of zeroes to the end of the image casper-rw. Make sure you use >> (append) and not > (overwrite).
```
dd if=/dev/zero bs=1M count=500 >> casper-rw
```

2. resize the filesystem to cover the entire image file
```
resize2fs casper-rw
```

That should be it.

---

### Post by DanyX on 2009-05-03
Cool, I will try that. Thanks a lot for your quick help!

---

### Post by cyberchango on 2009-07-13
rodrigo@ubuntu:~/e2fsprogs-1.41.7/build$ e2fsck -f /media/disk/casper-rw
e2fsck 1.41.7 (29-June-2009)
Paso 1: Verificando nodos-i, bloques y tamaños
Paso 2: Verificando la estructura de directorios
Paso 3: Revisando la conectividad de directorios
Paso 4: Revisando las cuentas de referencia
Paso 5: Revisando el resumen de información de grupos
/media/disk/casper-rw: 5106/129024 ficheros (11.3% no contiguos), 515838/515892 bloques
rodrigo@ubuntu:~/e2fsprogs-1.41.7/build$ resize2fs /media/disk/casper-rw 
resize2fs 1.41.7 (29-June-2009)
Por favor ejecute antes 'e2fsck -f /media/disk/casper-rw'.

Ok, now they are both the same version, I'm having the same problem :(

---

### Post by geirha on 2009-07-13
I don't understand that language. Could you turn off translations and paste again? Type in a terminal: ```
export LANG=C
``` After that, all commands run in that same terminal will not be translated (i.e. they'll be in english, which I can understand).

---

### Post by GeoffreyTransom on 2009-08-26
Hi there gierna

It's just e2fsck output, then the output of resize2fs... indicating that when he ran resize2fs it told him to run e2fsck again.

I get the same thing (in English, though), even after going through the entire rigmarole at [this link on HowToForge]("http://http://www.howtoforge.com/linux_resizing_ext3_partitions").

I'm running 9.04 (2.6.28-15-generic #49) on my desktop, and 2.6.28-13-generic on the USB stick (the stick kernel number cis from memory).

Cheers


GT

also, maybe it should have been made really clear for newcomers that they ought to only work on a copy of their casper-rw (I know you mentioned it)... it's basic common sense but it's surprising how often folks forget to do it (work on a backup).

Also, the thing I liked about DanDNSmith's solution was the it showed that you can mount casper-rw from within (say) a desktop install. I hadn't known that.

---

