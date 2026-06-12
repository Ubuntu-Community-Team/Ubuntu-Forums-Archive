---
title: "Grub"
date: 2009-08-28
forum: Desktop Environments
---

### Post by Murderface89 on 2009-08-28
Hi guys,

I'm running a dualboot system ubuntu/xp now for quite a while now.
But yesterday i wanted to install the new win7 so i did and it runs perfectly, You already know what happened... my Grub has gone and i can only boot into 7

i found a lot of articles on how to restore grub but since i read so many different things i kinda get confused about it.

I know i can restore my grub with a live CD but how do i set the partitions like what is where? i mean does it find it automatically? do i have to write it manually?

My disc setup is as followed:

hd0,1  -> win7
hd0,2  -> xp restore partition
hd0,3  -> seems to be like 1gb useless disc space
hd0,4  -> Ubuntu 9.04 all fully updated
hd0,5  -> Linux swap

I know i most likely have to install grub in hd0,4 But how do i get the entry's for my XP restore and my win7? last thing i want is too loose my Ubuntu install:biggrin:

so link me or help me out if you can plz :D

Thnx,
Kind regards,

---

### Post by rrplay on 2009-08-31
here is the link for you [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

previously > I know i most likely have to install grub in hd0,4 But how do i get the entry's for my XP restore and my win7? last thing i want is too loose my Ubuntu install

 notice from the guide grub gets installed into the mbr

also Note  that for GRUB, partitions start at 0 and not 1. for example 0=Partition 1, 1=Partition 2 and so on.

your Win7 is (hd0,0) in grub!

after booting back into Ubuntu the grub menu.lst file is located in /boot/grub/menu.lst

so as root carefully edit this file $ sudo gedit /boot/grub/menu.lst


```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7 
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


```

if you want to change the timeout [10 seconds] and keep from pressing the ESC at every boot change these

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```


hope this helps you out

---

