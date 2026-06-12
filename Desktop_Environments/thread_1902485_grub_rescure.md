---
title: "grub rescure"
date: 2011-12-30
forum: Desktop Environments
---

### Post by forsubhi on 2011-12-30
I use gparted to change size of file system from live cd then after I reboot I recieve this :
grub rescue>
how could I rescue my system ?

---

### Post by dentaku65 on 2011-12-30
> **forsubhi said:**
> I use gparted to change size of file system from live cd then after I reboot I recieve this :
grub rescue>
how could I rescue my system ?

I suggest to use Super Grub2 on USB key (SG2 is a mini-mini distro)
[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by forsubhi on 2011-12-31
thank you very much for easy solution

---

### Post by forsubhi on 2011-12-31
how to make this thread solved I forgot how ?

---

### Post by forsubhi on 2011-12-31
you should write this command after using the cd to boot 


$ grub-install <target>

target is your hard example sda - sdb -hd1

---

