---
title: "&quot;Factory&quot; Inspiron E1505n GRUB menu.lst"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by mark on 2007-06-19
Does anybody out there have a copy of the "factory" GRUB menu.lst file for the Inspiron E1505n laptop?  I did a clean 7.04 install (preserving the /OS and /DellUtility partitions) to set up my preferred partition scheme - and I forgot to save a copy.  Basically, I just want to include the "restore to factory defaults" option at boot time...

Thanks!

Mark

---

### Post by Mlehliw on 2007-06-19
Is there any good reason to keep those dell partitions around? I was planning on just wiping the hard drive clean, but I want to make sure I won't be missing anything later on.

---

### Post by kidcharles on 2007-06-19
Here is the important part of my menu.lst. If you have wiped the hard drive the option to reinstall will not work. Also depending on your partitions now this list may be pretty useless. Note that I X'ed out some long hexidecimal strings that I imagine are specific to my machine (after "UUID=") because who knows, they might be important private information.

```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=XXXXX ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=XXXXX ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=XXXXX ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=XXXXX ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz

```

---

### Post by mark on 2007-06-20
kidcharles, thank you.  That last bit, "Reinstall Operating System" is exactly what I was looking for (I wasn't sure if they chained to a DOS bootloader or what).  As I mentioned, I didn't wipe the drive - I kept the /OS and /DellUtility partitions, just redid the "working" partition scheme more to my liking...

Mlehliw, I wanted to retain the ability to restore my laptop to the "factory" configuration.  I don't *know* that Dell would balk at providing warranty service (if needed) due to a non-standard partitioning scheme, but why take chances?  Plus, the diagnostics from /DellUtility seem pretty thorough, from my one quick run through them.

---

