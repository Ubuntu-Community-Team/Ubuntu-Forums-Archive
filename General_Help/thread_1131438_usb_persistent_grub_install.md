---
title: "usb persistent grub install"
date: 2009-04-20
forum: General Help
---

### Post by flyingsliverfin on 2009-04-20
heres my situation: I have a mem stick with ubuntu 810 persistent (used this guide [http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/) ) on it.

first partition is fat16, second is ext2

 I used syslinux like in the guide, but I like grub better becuz then I can choose what to boot: my hdd or my usb stick (and  was planning to put UBCD on ther too, so I could maybe boot that too)

I tried to just copy the /boot/grub from my hdd to the /boot/ in the ext2 partition, but it didn't work. what do I need to do or what am I doing wrong? (I think that I should put the /boot/grub onto the fat16 partition, but there is no normal structure there like on the computer)

---

### Post by buck2825 on 2009-04-24
I don't know what your final destination for using the thumb drive is but, if you remove all hard disk from a system and use a install cd you can install easily to the thumb drive a full version of ubuntu.  just set up your partitions before starting.  I had 8.10 on a 8gb /dev/sdx1 fat16 3.5gb storage, /dev/sdx2 4gb ext2 /, and the rest as swap.  

now I am using portable ubuntu for what I want (ubuntu apps inside windows machines)

hope this helps

---

### Post by flyingsliverfin on 2009-04-24
ok

ty

---

