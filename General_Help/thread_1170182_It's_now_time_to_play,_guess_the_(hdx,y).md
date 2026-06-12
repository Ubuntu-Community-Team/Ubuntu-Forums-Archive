---
title: "It's now time to play, guess the (hdx,y)"
date: 2009-05-26
forum: General Help
---

### Post by themostunoriginalname on 2009-05-26
Hi all

I installed Vista today and have trouble trying to get grub to work with it.

Here's a copy of fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6855e55d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         369     2963961   82  Linux swap / Solaris
/dev/sda2             370        4867    36130185    5  Extended
/dev/sda3   *        4868        9730    39055360    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5             370        4867    36130153+  83  Linux


Here's a copy of the entry I wrote into /boot/grub/menu.lst

title		Windows Vista
rootnotify	(hd0,2)
makeactive
chainloader 	+1

I have tried (hd0, x) where x is any integer from 0 to 4 and all of them has not worked at all. Any ideas what it can be?

Thanks in advance. Whoever wins get an imaginary cookie.

---

### Post by KhurramM on 2009-05-26
use SGD

It might help resolve your issue. Best of luck.:popcorn:

---

### Post by c/Kr3t on 2009-05-26
> **themostunoriginalname said:**
> Hi all

I installed Vista today and have trouble trying to get grub to work with it.

Here's a copy of fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6855e55d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         369     2963961   82  Linux swap / Solaris
/dev/sda2             370        4867    36130185    5  Extended
/dev/sda3   *        4868        9730    39055360    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5             370        4867    36130153+  83  Linux


Here's a copy of the entry I wrote into /boot/grub/menu.lst

title		Windows Vista
rootnotify	(hd0,2)
makeactive
chainloader 	+1

I have tried (hd0, x) where x is any integer from 0 to 4 and all of them has not worked at all. Any ideas what it can be?

Thanks in advance. Whoever wins get an imaginary cookie.



Scenario 1
You've installed windows on a separate partition and you think everything is all dandy. You reboot to log into ubuntu, and it boots to windows instead, oh noes! ikr? Here's how to fix it.

Boot into your liveCD

Start your terminal and type:
Code:

sudo grub

find /boot/grub/stage1

the number you see, probably (hd0,2) is where the grub loader was before.

type out...
Code:

root (hd0,2)

setup (hd0)

quit

exit

That SHOULD bring it back up..if not continue reading.

If that did not restore your grub menu then do this instead.
(credit goes to Peter Upfold at [http://fosswire.com/post/2009/5/rest...rwritten-grub/](http://fosswire.com/post/2009/5/rest...rwritten-grub/))

Boot to your liveCD

Open terminal and type:
Code:

sudo mkdir /mnt/system

sudo mount /dev/<your ROOT partition> /mnt/system

sudo -i

mount -o bind /dev /mnt/system/dev

chroot /mnt/system

grub-install /dev/sda

that should take care of the problem.

Scenario 2
You startup your computer and it loads to the grub menu. You press enter to go into your ubuntu partition but it says Error 17: Cannot mount that partition. You pretty much have a heart attack, but worry not for you are reading this thread.

You do most of what Peter Upfold suggested but you detour in the middle.


Boot to your liveCD

Open terminal and type:
Code:

sudo mkdir /mnt/system

sudo mount /dev/<your ROOT partition> /mnt/system

sudo gedit /mnt/system/boot/grub/menu.lst

from here you see the coding of your GRUB menu. scroll down till you see ## ## End Default Options ##

right after that is where it shows the text output on your GRUB menu

in each segment there is an option called root and it show (hd0,<whatever>)

in the terminal type

Code:

sudo grub

find /boot/grub/stage1

and replace whatever number that is in the root option with the number you get with that command.

save, exit and reboot and it should be all good.

---

### Post by c/Kr3t on 2009-05-26
i just hurridly copy pastad that from a walkthrough i wrote. hope it helps

---

