---
title: "PC Linux broke Kubuntu, please tell me..."
date: 2006-05-30
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-05-30
While installing PC Linux to my second hard disk, I accidently pulled an idiot and installed LILO to hda1 (Kubuntu)'s boot sector. Since then, I've been unable to boot Kubuntu. I can boot Ubuntu (hdb7) and PC Linux (hdb5) but not Kubuntu (hda1). Is there a way to recover or repair the installation without re-installing?

---

### Post by Sef on 2006-05-30
Follow the instructions here:

[Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by Wr8EYilK8Y on 2006-05-30
I installed Ubuntu to the system and that restored the GRUB. It looks sorta like this (the menu does) because I edited the file so I can read it more easily (titles and positions moved around a bit). The whole names are left out for ease of reading.
```

pclinuxos
Ubuntu Linux:
Ubuntu kernel
Ubuntu kernel (recovery)
Kubuntu Linux k7:
Kubuntu kernel (k7) (broken)
Kubuntu kernel (k7) (recovery) (broken)
Kubuntu Linux 386 (to be removed):
Kubuntu kernel (386) (broken)
Kubuntu kernel (386) (recovery) (broken)
Memtest:
Kubuntu Memtest x86 (broken)
Ubuntu Memtest x86

```

---

### Post by Jucato on 2006-05-30
What problems are you still encountering? It would also be good if you could post the contents of your menu.lst (at least the ones starting from the first bootable entry).

---

### Post by Wr8EYilK8Y on 2006-05-31
I'll post those but here's what happens when I try to boot. Kubuntu begins to boot. Then, it gets to 1 step (I've never written down the error) and begins errors about /proc and mounting tmpfs in /tmp and stuff, then stops.

---

### Post by Wr8EYilK8Y on 2006-05-31
Menu.lst:
```

title		pclinuxos Linux release 2005 (Texstar) for i586 (on /dev/hdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.12-oci6.mdk-i586-up-1GB root=/dev/hdb5 
savedefault
boot


### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu Linux:
root

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb7 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb7 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Kubuntu Linux k7:
root

title		Kubuntu, kernel 2.6.12-10-k7 (broken)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

title		Kubuntu, kernel 2.6.12-10-k7 (recovery mode) (broken)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Kubuntu Linux 386:
root

title		Kubuntu, kernel 2.6.12-10-386 (broken)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Kubuntu, kernel 2.6.12-10-386 (recovery mode) (broken)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Memtest:
root

title		Kubuntu, memtest86+ (broken)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		Ubuntu, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin  
boot

```

---

