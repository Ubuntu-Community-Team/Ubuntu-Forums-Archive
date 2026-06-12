---
title: "Update messed up grub"
date: 2006-07-14
forum: Desktop Environments
---

### Post by lastrite on 2006-07-14
Prior to updating I had my system dual booting windows for gaming as well as ubuntu. Windows was at the top of my boot.lst but now it has been removed, I had a go at manually adding it but something isn't right ](*,)

Currently it is set as follows within menu.lst:

```
title		Microsoft Windows XP
root		(hd2,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

```

Here's some more info: 

```
(hd0)	/dev/hda
(hd1)	/dev/hdd
(hd2)	/dev/sda
```

This is the drive with my windows partition on it:

```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   489661199   244830568+   7  HPFS/NTFS
/dev/sda2   *   489661200   582115274    46227037+  83  Linux
/dev/sda3       582115275   586099394     1992060    f  W95 Ext'd (LBA)
/dev/sda5       582115338   586099394     1992028+  82  Linux swap / Solaris


```

Please help :cry: 

Thanks

Edit: Sorry wrong section please move ](*,)

---

### Post by philippe_carlo on 2006-07-14
Seems like there is a Linux installed on the dsa too and the bootable flag there is set to sda2! Should you not change the grub entry to:
```

title		Microsoft Windows XP
root		(hd2,2)
savedefault
makeactive
chainloader	+1

```

---

### Post by Herman on 2006-07-14
@lastrite, Whoever advised you to place your Windows operating system entry at the head of your debian automagic kernels list gave you a bum steer. Quite a number of new users copy their Windows entry there as an easy way to make Windows boot as the default operating system. You can go make a cup of coffee and if no-one makes a selection from the GRUB menu during boot-up and it times out, Windows will be booted by default right?
...until you get an update with a new kernel and the automagic kernels list does what it was designed to do and updates itself and deletes all the entries that aren't supposed to be there.](*,)

:D Okay, here's the right way to do it. Place your Windows back at the bottom of your menu.lst file, under the divider that seperates the automagic kernels list from the 'other operating systems'. Windows is an 'other operating system'.  That's where it was when Ubuntu was installed and that's where it's supposed to stay. That way it will be left alone next time the automagic kernels list gets updated because a new kernel has been added to Ubuntu.
Then, do the following, [*click here*]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc").

I hope this helps you, regards, Herman :D

---

### Post by lastrite on 2006-07-14
Thanks for the fast replies.

Yeah it was a bit naughty of me doing that :oops: 

Now to me it seems logical to assume it should be hd2,0 as that is my 300GB Sata drive and my windows install would be on the first partition. I've tried it with numerous other settings just to be sure from within grub:

hd2,0 = Filetype unknown, Partition type 0x7
hd2,1 = error 12 invalid device requested

And I've tried hd0,0-hd4,4 just for the sake of it and it doesnt want to boot.

My windows partition is definately intact as I used it prior to updating ubuntu and all files remain on it.

My menu.lst reads as follows now:

```
title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-k7
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:

title		Microsoft Windows XP
root		(hd2,0)
savedefault
makeactive
chainloader	+1
```

I suppose I could use the ubuntu install cd & skip to the install of grub that should work shouldnt it?

---

### Post by Herman on 2006-07-14
lastrite, I agree, hd0,2 seems to me ike the correct way to designate your Windows in your grub/boot/menu.lst too. I can't see what's wrong with that menu.lst anymore now.

Maybe try 'rootnoverify' instead of 'root' ?
Also I notice a small detail where yours differs from mine, I'm not sure if it's critical or not, but mine has an additional word 'root' placed under 'title  Other operating systems. Those two lines could be active as they don't have a # mark before them, so that might be something important too.

```
              ### END DEBIAN AUTOMAGIC KERNELS LIST
                   
             # This is a divider, added to separate the menu items below from the Debian
             # ones.
             title        Other operating systems:
             root
                   
                   
             # This entry automatically added by the Debian installer for a non-linux OS
             # on /dev/hda1
             title        Microsoft Windows XP 
             rootnoverify        (hd0,2)
             savedefault
             makeactive
             chainloader    +1
```

---

### Post by lastrite on 2006-07-14
Managed to fix it using the alternate ubuntu installer to reinstall grub.

Turns out these mappings were required: 

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

Thanks for the help :mrgreen:

---

### Post by Herman on 2006-07-14
That's great ,congratulations and good work! :D
I am happy to read that you solved your problem, only I wish I had thought of that for you! :D

Well done!:D
Regards, Herman

---

