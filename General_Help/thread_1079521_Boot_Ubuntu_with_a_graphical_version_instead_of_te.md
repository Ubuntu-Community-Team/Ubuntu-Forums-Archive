---
title: "Boot Ubuntu with a graphical version instead of text mode"
date: 2009-02-24
forum: General Help
---

### Post by arepaking on 2009-02-24
Hello experts,
A long time ago I did a change somewhere and my ubuntu started to boot in a text mode. I am able to see the "Ubuntu" logo and the orange progress bar at the very beginning, but after a few seconds and enter in this text mode that begins the processing saying:

*Reading files to boot (or something like this) 

Then, it starts to show all the background initialization process until the logon screen appears.

Does anyone knows how can I prevent the text mode from appearing? I just want to see the orange progress bar.

Thanks in advance,
AK

---

### Post by Wayne_V on 2009-02-24
Were you changing /boot/grub/menu.lst?   Do your kernel entries have "quiet splash" on them:

$ grep "^kernel" /boot/grub/menu.lst

---

### Post by arepaking on 2009-02-24
> **Wayne_V said:**
> Were you changing /boot/grub/menu.lst?   Do your kernel entries have "quiet splash" on them:

$ grep "^kernel" /boot/grub/menu.lst

Hi Thanks for your reply.

This is how my menu.lst looks like:

## ## End Default Options ##
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=16d08531-1119-444e-b426-e715ac675d4d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=16d08531-1119-444e-b426-e715ac675d4d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=16d08531-1119-444e-b426-e715ac675d4d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=16d08531-1119-444e-b426-e715ac675d4d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet
```

---

### Post by Wayne_V on 2009-02-24
That should be right I would think.   Is one of your init.d scripts returning non zero?  That may kick it from graphical to text boot mode.  Any error displayed right when it switches?

---

### Post by arepaking on 2009-02-24
hmmm is hard to tell since every thing happens very quickly. I don't remember seeing any errors reported.

---

### Post by todak on 2009-02-24
Check [here]("http://ubuntuforums.org/showthread.php?t=1038055") and see if this will help. If you dual-booted with another distro and it used your existing swap file, chances are that is why you do not have a boot splash.

---

