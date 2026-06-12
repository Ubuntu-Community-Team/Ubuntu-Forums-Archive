---
title: "How to reinstall Grub"
date: 2005-07-07
forum: Desktop Environments
---

### Post by tikal26 on 2005-07-07
So I messed up again and reinstalled windows ( I need it for Rhino 3d) and it rewrote my MBR now I don't know how to get back to Ubuntu. any ideas

---

### Post by manicka on 2005-07-07
[http://www.ubuntuforums.org/showpost.php?p=242484&postcount=3](http://www.ubuntuforums.org/showpost.php?p=242484&postcount=3)

---

### Post by tikal26 on 2005-07-09
I don't know how to mount the partition. When I boot from the CD I get to the partition manager. 
Whne i  type rescue whe prompt to boot and then I selects the root partion and i type grub install i get an erro message taht says unable to start bterm.
any other way. I really don't want to loose my work.

---

### Post by az on 2005-07-09
Once you have chosen your keyboard and all the hard drive and cdrom drivers hae been loaded hit CTRL-ALT-F2 and then

mount /dev/hda5 /mnt

ls /mnt
(to see if you have it right)

chroot /mnt
grub-install /dev/hda

reboot

---

### Post by oliwally on 2005-07-10
I had a similar problem and received excellent help. Check it out at [http://ubuntuforums.org/showthread.php?t=43528&page=4&pp=10](http://ubuntuforums.org/showthread.php?t=43528&page=4&pp=10)

Especially creating a Grub boot floppy as described was just magic.

---

### Post by tikal26 on 2005-07-11
Azz:
Ok so I'm not a linux exper. and before I do anything crazy I'm wondering if hda5 is what i have to type or do I have to substitute that for my root partition. 
just wondering before i do anything crazy

---

### Post by tikal26 on 2005-07-15
?

---

### Post by manicka on 2005-07-15
[QUOTE=tikal26]?[/QUOTE]
 If you could make the question a little clearer then that would help.

Do you mean what do I type for a mount point in the partitioner? For your main partition you just type / . If you are setting up other partitions for your home directory etc, you would type /home, /tmp, /user etc.

HTH

---

### Post by tikal26 on 2005-07-15
The question is meant for the comments that azz made above. I have four partition on my drive and I am wondering if when he has hda5 he means my root partition

---

### Post by Irony on 2005-07-19
I've got to reinstall Grub on my MBR as well and am wondering what

*mount /dev/hda5 /mnt*

actually refers to. I assume hda0 would be the mount point so why hda5 - I've got 4 partitions on my hard drive.

---

