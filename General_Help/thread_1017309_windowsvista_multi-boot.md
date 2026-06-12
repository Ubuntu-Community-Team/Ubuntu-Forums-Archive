---
title: "windows/vista multi-boot"
date: 2008-12-20
forum: General Help
---

### Post by ibootindos on 2008-12-20
so I used to have grub loader with Ubuntu 9.04 and Windows Vista running. Then Windows crashed, so I did the windows restore, and now I can't get to my Ubuntu! it reminds me of that joke "play a microsoft cd backwards it plays satanic music, but that's nothing, play it forward and it installs windows" lol. but seriously, I installed windows on one hard drive, and ubuntu on another, so I know ubuntu is still there, I just need help on reinstalling grub. thanks

---

### Post by TeXtonyx on 2008-12-20
Super Grub Disk will boot Ubuntu, I use it with help enabled.

If Ubuntu is on your second drive, sdb, I think you might
want grub in the MBR, which is (hd1)^ in grub speak.

Boot from the Ubuntu live cd and from a terminal type:

sudo grub

grub> find /boot/grub/stage1

grub> root (hd1,0) (use the result from what find reports)

I tend to think your stage1 grub files will be in /boot/grub
on hd1 which is your second drive or sdb. I suppose it's 
possible that those files are located on hd0 or sda, but I doubt it.

grub> setup (hd1) (puts grub in the MBR of the second drive)

grub>quit

If you want grub installed to the /boot partition inside of the
Ubuntu partition you would use something like grub>setup (hd1,0)
which second drive first partition, the numbers are one lower than
sdb1 where one is the partition number. sdb2 = (hd1,1) etc, 

Now if you want to boot directly to Ubuntu after you install
it in the MBR of the second drive, change your default boot
drive in the bios, from hd0 (first drive) to hd1 (second drive).
One other useful command is sudo fidsk -l (small L) which displays
partition information.

---

### Post by klein de usa on 2008-12-21
hi 
do you have the live ubuntu 8.04 cd ?

read this [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

i know it is there i have used it a couple of times my self.

---

### Post by ibootindos on 2008-12-21
yeah, thanks guys. I'll give that a shot and let you know how it works.

---

