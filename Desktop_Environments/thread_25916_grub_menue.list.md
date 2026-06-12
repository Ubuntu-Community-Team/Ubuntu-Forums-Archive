---
title: "grub_menue.list"
date: 2005-04-11
forum: Desktop Environments
---

### Post by devil28 on 2005-04-11
hi all,
I installed kubuntu yesterday and during install I got the message that grub would pick up my winxp and another linux disrto(simply mepis). what it did was xp, kubuntu and 2 instances of memtest instead of memtest + mepis. so I changed menue.list back to mepis and xp, and now I need the correct line for kubuntu to add to the list (xp has got the chailoader +1 argument, does kubuntu need chainloader +2? ; what is the exact kernel- version for kubuntu 5.04 final? and so on)

thx

edit: how about this one:
title kubuntu 5.04 on hdd11, Kernel 2.6.10
kernel  (hd1,10) /boot/vmlinuz-2.6.10 root=/dev/hdd11 nomce psmouse.proto=imps quiet splash=verbose vga 791
initrd (dh1,10)/boot/initrd.splash
chainloader +1

is that correct?

---

### Post by dmh-bidlah on 2005-04-11
I think under a debian based distro youcan just
```
$ sudo update-grub
``` to automagically detect all of your OS-es and kernels

---

### Post by abovett on 2005-04-11
[QUOTE=devil28]
edit: how about this one:
title kubuntu 5.04 on hdd11, Kernel 2.6.10
kernel  (hd1,10) /boot/vmlinuz-2.6.10 root=/dev/hdd11 nomce psmouse.proto=imps quiet splash=verbose vga 791
initrd (dh1,10)/boot/initrd.splash
chainloader +1

is that correct?[/QUOTE]

Not quite. You don't need chainloader - that's for Windows etc where it has to chain to another loader. 

In case the automatic update doesn't do what you want and/or you prefer to maintain your GRUB file manually, here's mine as an example. It's called ubuntu rather than kubuntu but at this level they are the same (in fact both sets of packages are installed on this machine).

```

title           Ubuntu, kernel 2.6.10-5-686
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/hda8 ro resume=/dev/hda7 quiet splash
initrd          /boot/initrd.img-2.6.10-5-686
savedefault
boot

```

Hope that helps

Andy B

---

### Post by devil28 on 2005-04-11
this doesnt seem to work. I always get error 15, file not found
 heres my entry:

[COLOR=DarkOrange]title           Ubuntu, kernel 2.6.10-5-686
root            (hd1,10)
kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/hdd11 ro  quiet splash=verbose vga=791
initrd          /boot/initrd.img-2.6.10-5-686
savedefault
boot[/COLOR]

home is on hdd10, root on hdd11
I have both entries for both distros in both menue.lists. is that correct or do they belong only in their own list?
cant think of any more mistakes, so whats wrong please?

thxx

---

### Post by devil28 on 2005-04-12
anyone, please?

---

