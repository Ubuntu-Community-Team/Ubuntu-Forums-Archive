---
title: "Having windows installed 2nd."
date: 2005-10-13
forum: Desktop Environments
---

### Post by Dillius on 2005-10-13
I am switching over to Ubuntu as my new Linux Desktop. With my previous version, I had to use special codes to configure GRUB to properly trick Windows into booting, because it was not the first OS installed and was not on the first hard drive. There were a series of codes that I can not remember, but they basically tricked windows into thinking it was on the main hard drive. Does anyone know the code you have to put in grub.conf for this to work? It's been a while and I can't remember where I found it.

---

### Post by jasongrieves on 2005-10-13
in /boot/grub/menu.lst

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		2
```

then for your bootup OS's
```

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

```

This tells grub to boot Windows first....

Is this what you are talking about?

---

### Post by leezer3 on 2005-10-13
No, it's not (I think :razz: )
You need to know the number of the partition that Windoze is on (Use lsparts or gparted), and then modify the Windoze entry in Lovechild's post to suit, so if it was on the 2nd hard-disk, partition 0 then it would look like:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
```

And so on

Cheers

-Leezer-

---

### Post by Dillius on 2005-10-14
Yea makeactive and chainloader were what I was looking for. It'll be hd(1,1) for me I'm pretty sure, but mainly I just wanted to be sure of those commands.

---

