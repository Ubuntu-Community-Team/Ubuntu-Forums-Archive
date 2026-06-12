---
title: "Fusing partitions in arch."
date: 2009-06-17
forum: General Help
---

### Post by dragos240 on 2009-06-17
I was at school and someone asked how many gigs my netbook had on it, I looked it up, and / was only 2.5gb, this didn't make much sense at all, so I looked at the partitions and / was only 8gb, and /boot and /home contained the rest of the space, can I fuse / /boot/ and /home together in one partition? I tried to unmount /home, and it was busy T_T.

---

### Post by ptn107 on 2009-06-17
You can manually but that's a complicated process.  An easier option for you (if erasing everything is ok) is to reinstall Ubuntu and choose 'Guided - use entire disk' from the partition page.  That will put everything under root (/).

Honestly keeping your personal documents and whatnot (/home) separate is the better way to go.  I'd leave everything where it is.

---

### Post by dragos240 on 2009-06-18
> **ptn107 said:**
> You can manually but that's a complicated process.  An easier option for you (if erasing everything is ok) is to reinstall Ubuntu and choose 'Guided - use entire disk' from the partition page.  That will put everything under root (/).

Honestly keeping your personal documents and whatnot (/home) separate is the better way to go.  I'd leave everything where it is.

But I'm not using ubuntu! I'm using arch..... archlinux.

---

### Post by dragos240 on 2009-06-25
Bump

---

### Post by Nepherte on 2009-06-25
I wouldn't merge them at all. Having several partitions for important parts of your system has multiple advantages over 1. For you, the most important advantage would be that when your system crashes (this is related to /), you can still keep all your personal data (/home) while reinstalling your system.

---

### Post by dragos240 on 2009-06-25
> **Nepherte said:**
> I wouldn't merge them at all. Having several partitions for important parts of your system has multiple advantages over 1. For you, the most important advantage would be that when your system crashes (this is related to /), you can still keep all your personal data (/home) while reinstalling your system.

How can I resize the partitions? Can I get parted magic on a usb key?

---

### Post by Tyke91 on 2009-06-25
try gparted
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by dragos240 on 2009-06-25
I tried gparted but none of them will unmount, it seems they're all mounted at boot, and cannot be unmounted, I am working a netbook here, so I do not have a cd drive on it, can I use parted magic on a usb drive?

---

### Post by Tyke91 on 2009-06-25
you can't resize a partition that you are currently using :) that would corrupt stuff to hell and back....


burn the gparted liveCD or put it on a usb drive and boot from it. It will boot into a custom gentoo system that only runs Gparted

---

### Post by bodhi.zazen on 2009-06-25
If it is not broken, don't fix it.

You should manage your partitions from a live CD or USB as you will not be able to resize a mounted partition, in your case /home

Second, take the time to understand what you are doing, lol.

You are probably best off using tar to archive /boot and /home and move them to /

If you put /home and /boot on the same partition, separate from / , you will have issues as you will need to mount the same partition at both /boot and /home at the same time.

In theory you could simple boot from the partition and not mount it a /boot, but this makes upgrades difficult.

You can also use mount --bind to mount the partition at both /boot and /home , but as you can see it is getting a bit complex.

After you move your partitions you will need to re-configure grub.

If you can not easily boot from a usb or cdrom you can easily be stuck with an un bootable system, lol.

---

### Post by dragos240 on 2009-06-26
Thank you everyone, but things aren't perfect. I moved both partitions and their contents to the root directory partition, although, my next task is to stop arch from automatically mounting what are normally mounted as /home and /boot, I don't think they are in /etc/rc.conf but i'll check. Thanks.

---

### Post by bodhi.zazen on 2009-06-26
partitions are managed in /etc/fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by dragos240 on 2009-06-26
> **bodhi.zazen said:**
> partitions are managed in /etc/fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

Just out of curiosity, whats the difference between fstab and mtab.

---

### Post by unutbu on 2009-06-26
/etc/fstab is a configuration file that controls how partitions are to be mounted.

/etc/mtab records information about partitions that are currently mounted.
It is the same as the output you see when you type "mount".

---

### Post by dragos240 on 2009-06-26
> **unutbu said:**
> /etc/fstab is a configuration file that controls how partitions are to be mounted.

/etc/mtab records information about partitions that are currently mounted.
It is the same as the output you see when you type "mount".

Thanks

---

### Post by dragos240 on 2009-06-26
Everything is in one partition and everything works now, except swap, other than that, everything works perfectly! Thanks!

---

