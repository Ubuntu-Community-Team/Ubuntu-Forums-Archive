---
title: "boot Help /dev/sda1 failure"
date: 2009-01-25
forum: General Help
---

### Post by dta983 on 2009-01-25
Hey,

I tried to boot up ubuntu on my sony vaio laptop and i got the message: "/dev/sda1 contains a file system with errors, check forced ... Unexpected inconsisteny; run fsck manually. .... An automatic file system check of the root filesystem failed. A manual fsck must be performed..." ubuntu has been running fine for about 3 months. can anyone tell me what the problem is or how i should fix it? Thanks!

---

### Post by caljohnsmith on 2009-01-26
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition, and then do:
```
sudo fsck -yCM /dev/[COLOR="Blue"]sdaX[/COLOR]
```
But replace sdaX with the Ubuntu partition, and please post the output.

---

