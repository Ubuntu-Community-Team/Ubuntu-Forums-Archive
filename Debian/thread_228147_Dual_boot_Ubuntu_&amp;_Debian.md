---
title: "Dual boot Ubuntu &amp; Debian"
date: 2006-08-02
forum: Debian
---

### Post by dolby on 2006-08-02
i am about to have a dual boot with 2 linux os's for the first time & thought i'd ask before going on to that.

my current partition scheme is: 

```

/dev/hda1  /boot   ext2 (100mb)
/dev/hda3  /       ext3
/dev/hda4 /mnt/a   ext3
/dev/hda5 swap 
```

and i want to install debian on /dev/hda4.
i will use the same swap but what about /boot?
can i use the same or should i install all files to /dev/hda4?
or should change the partion scheme (beyond /dev/hda4)?

also i know that the debian installation will try to mess with 
grub but im think not to install a bootloader and mannually add 
an entry to grub later through ubuntu when the debian installation will be over.

my current menu.lst is:

```

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-k7 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.15-26-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-k7 root=/dev/hda3 ro single
initrd		/initrd.img-2.6.15-26-k7
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
```

will adding an entry like this do the trick?

```

title		Debian, kernel x.x.x
root		(hd0,**3**)
kernel		/vmlinuz-x.x.x root=/dev/hda**4** ro quiet splash
initrd		/initrd.img-x.x.x
boot
```

---

