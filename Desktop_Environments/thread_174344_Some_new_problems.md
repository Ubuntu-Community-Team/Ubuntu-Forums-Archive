---
title: "Some new problems"
date: 2006-05-11
forum: Desktop Environments
---

### Post by Rhapsody on 2006-05-11
I've done 'Full Upgrade' in Adept, which has left me with a couple of problems and oddities.

1) Most obviously, my hard drives and DVD-rewriter are gone. I can still access them, but when I look under 'Storage Media' (doesn't matter if this is in Konqueror or another application), all that's listed is my floppy drive. The files can clearly be accessed (otherwise Kubuntu wouldn't boot) but they're invisible. I'd prefer to figure out why this is happening and fix it before doing anything else.

2) New options have appeared in GRUB for 'Ubuntu kernel 2.6.10-10' (or something similar), which is now the default ('Ubuntu kernel 2.6.10-9' is still there, but no longer the default). This would be fine, except the steps that I took to enable my MODEM (found [here](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html), and very useful) seem to have been lost, as it doesn't work. I'm fairly confident I can fix this, but was that supposed to happen?

3) Assuming I can get 'Ubuntu kernel 2.6.10-10' working entirely, how would I go about safely removing 'Ubuntu kernel 2.6.10-9'?

4) Was using that 'Full Upgrade' button something I was not supposed to do?

---

### Post by louis_nichols on 2006-05-11
1. They're probably not listed in fstab anymore. post here the contents of file /etc/fstab

2. You can make your previous kernel boot as a default again (you can just as well choose it from the list in the grub boot menu, but I don't think it's what you are looking for). What you have to do is open for editing, as root, the grub menu file:
```
sudo gedit /boot/grub/menu.lst
```

Now in there, after some options and explanations, you will have something like:

```
title		Ubuntu, kernel 2.6.15-21-k7
root		(hd0,2)
kernel		/vmlinuz-2.6.15-21-k7 root=/dev/mapper/kubuntu-root ro quiet splash vga=792
initrd		/initrd.img-2.6.15-21-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-21-k7 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.15-21-k7 root=/dev/mapper/kubuntu-root ro single vga=792
initrd		/initrd.img-2.6.15-21-k7
boot

title		Ubuntu, kernel 2.6.15-18-386
root		(hd0,2)
kernel		/vmlinuz-2.6.15-18-386 root=/dev/mapper/kubuntu-root ro quiet splash vga=792
initrd		/initrd.img-2.6.15-18-386
savedefault
boot
```

These entries are the kernels you can boot. Grub counts them starting from 0. So, in my case entry Ubuntu, kernel 2.6.15-18-386 will be 2. So, in your list, you'll have to find the kernel you want to boot, do the count and then search the option ```
default		0
``` and change 0 to your count made by the rule above. 

3.Then, reboot. To make the system freeze at the current kernel, you have to uninstall newer kernels, and then, in synaptic, select the one you want to freeze, go to menu option "package" and choose "lock version"

4. Definitely not! Upgrades are a necessary thing to do, for several reasons, the most important being system security and stability.

---

### Post by Rhapsody on 2006-05-14
[QUOTE=louis_nichols]1. They're probably not listed in fstab anymore. post here the contents of file /etc/fstab[/QUOTE]

Sorry, I've been distracted for a few days. But how do I do that?

---

### Post by ComplexNumber on 2006-05-14
[quote=Rhapsody]Sorry, I've been distracted for a few days. But how do I do that?[/quote]
either:
-go to /etc/fstab and type out the contents
-go to /etc/fstab and make a screenshot

---

### Post by Rhapsody on 2006-05-14
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
OK, so the drives I'd be expecting to see are listed there (I keep promising I'll do something about that NTFS partition), but Konqueror still isn't seeing anything.

---

