---
title: "Trouble properly mounting wotlk dvd"
date: 2008-12-30
forum: General Help
---

### Post by mr_x408 on 2008-12-30
hey guys im trying to install wrath of the linch king. Following this tutorial 
[http://silverpenpub.net/games/how-to-install-wrath-of-the-lich-king-on-linux](http://silverpenpub.net/games/how-to-install-wrath-of-the-lich-king-on-linux)
i am told to unmount the dvd and remount it with the following command

"sudo mount -t udf -o ro,unhide,uid=userid /dev/scd0 /media/cdrom0/"
but when i enter that i get
"mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
"
i learned that i have to change in this file using 
"
sudo gedit /etc/fstab
"
when i type that in i get...
"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8a74d0ad-2a5f-4be2-a800-6167cc568430 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=84ab3330-d0f1-4577-826c-4129466fd952 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0"
any suggestions guys?

---

### Post by dcstar on 2008-12-30
> **mr_x408 said:**
> hey guys im trying to install wrath of the linch king. Following this tutorial 
[http://silverpenpub.net/games/how-to-install-wrath-of-the-lich-king-on-linux](http://silverpenpub.net/games/how-to-install-wrath-of-the-lich-king-on-linux)
i am told to unmount the dvd and remount it with the following command

"sudo mount -t udf -o ro,unhide,uid=**userid** /dev/scd0 /media/cdrom0/"
........
any suggestions guys?

**userid** is YOUR user id.

---

### Post by mr_x408 on 2008-12-30
> **dcstar said:**
> Lose the unhide & uid stuff, that is not supported by Ubuntu mount.

I am surprised that it just doesn't mount when you insert it anyway.

It dose but for me to install it i have to unmount it and then mount it so it shows all of the hidden filles...
simply clicking view-> hidden files dosent show all the files on the disk

---

### Post by mr_x408 on 2008-12-30
> **dcstar said:**
> **userid** is YOUR user id.

thankyou for that:) ... now i feel dumb for not catching that before it worked
thanks for the replys

---

### Post by dcstar on 2008-12-30
> **mr_x408 said:**
> thankyou for that:) ... now i feel dumb for not catching that before it worked
thanks for the replys

Please read the end of my posts.

---

