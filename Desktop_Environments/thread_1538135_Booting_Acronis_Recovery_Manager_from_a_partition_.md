---
title: "Booting Acronis Recovery Manager from a partition using Grub Menu"
date: 2010-07-24
forum: Desktop Environments
---

### Post by oschoices on 2010-07-24
Hi all,

New to Ubuntu and trying to ensure I can boot into Acronis Recovery Manager to be able to reimage Windows as and when appropriate.  If I enable the Acronis Recovery Manager so that it overwrites the MBR then I run out of ROM I think which prevents it from loading.  If I use the software CD that doesn't detect my sata drive. However, I made a rescue CD in Acronis and this does work but I'm only using my bootable CD drive temporarily in this system.  

I found this post ([http://ubuntuforums.org/showthread.php?t=449167]("http://ubuntuforums.org/showthread.php?t=449167")) which seems to do what I would like and have managed to follow this to extract the files from my rescue CD into /boot/acronis.  However this original post relates to Grub and as a newbie to Ubuntu I think I have Grub2.  I can't figure out what the correct syntax is to make a new Grub Menu entry in /etc/grub.d/40_custom.

```
menuentry "Acronis True Image 10 Home"{
set root='(hd0,2)'
linux /boot/acronis/kernel.dat quiet vga=788 ramdisk_size=40000
initrd /boot/acronis/initrd
}
```

I've done the update-grub command to rebuild grub.cfg but the menu entry when I try it from the Grub menu gives me the errors;

error: file not found
error: you need to load the kernel first.

Any help please?

---

### Post by oschoices on 2010-07-24
Just a quick update...

I think as my /boot is on a separate partition and judging by other entries in grub.cfg that the /boot needed to be dropped from the paths, like so;

```
menuentry "Acronis True Image 10 Home" {
set root='(hd0,2)'
linux /acronis/kernel.dat
initrd /acronis/initrd
}
```

I no longer get the errors but I just get a black screen which takes me back to the pc rebooting.  Tried it with and without having the vga and ramdisk_size references. 

Giving up for tonight, I shall be dreaming terminal lingo already with the number of times i've typed "gksudo gedit /etc/grub.d/40_custom" etc..

---

