---
title: "[SOLVED] Installing Grub, trying to get a boot going"
date: 2008-12-16
forum: General Help
---

### Post by Het Irv on 2008-12-16
So I am trying to get a dual-boot going, between Fedora and Ubuntu, for work and for personal use respectively.  I have Fedora setup and working with a separate boot partition, but for some reason, I cannot get it to see Ubuntu.

fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bf0bcd4

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         247     1983996   83  Linux
/dev/sda2             248       14593   115234245    5  Extended
/dev/sda5             248        2800    20506941   83  Linux
/dev/sda6           14351       14593     1951866   82  Linux swap / Solaris
/dev/sda7            6448       14350    63480816   83  Linux
/dev/sda8            2801        6447    29294496   83  Linux
```

and menu.lst
```
title Fedora (2.6.27.7-134.fc10.i686)
	root (hd0,0)
	kernel /vmlinuz-2.6.27.7-134.fc10.i686 ro root=UUID=37defdf4-3131-4234-8860-172bc611af55 rhgb quiet
	initrd /initrd-2.6.27.7-134.fc10.i686.img
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,0)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=37defdf4-3131-4234-8860-172bc611af55 rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img
title Ubuntu
	rootnoverify (hd0,4)
	chainloader +1
```

Ubuntu is on /sda5, and I am getting Grub Error 13.
After looking for a little bit, I realized that I didn't install a boot loader when installing Ubuntu, so that I didn't overwrite the Fedora one. 

```
[root@CHR214664-Fedora hetirv]# ls /media/disk-1/boot
abi-2.6.27-7-generic         memtest86+.bin
config-2.6.27-7-generic      System.map-2.6.27-7-generic
grub                         vmcoreinfo-2.6.27-7-generic
initrd.img-2.6.27-7-generic  vmlinuz-2.6.27-7-generic

```

the grub there is just a folder I created when I was trying to install grub using the "sudo install-grub /dev/sda" with the Live CD, but that didn't work. Something about not finding /boot or it not being a block device.

Here is the other thread on the Fedora Forums that I have on this...
[http://forums.fedoraforum.org/showthread.php?p=1132522&posted=1#post1132522](http://forums.fedoraforum.org/showthread.php?p=1132522&posted=1#post1132522)

---

### Post by logos34 on 2008-12-16
> **Het Irv said:**
> I realized that I didn't install a boot loader when installing Ubuntu, so that I didn't overwrite the Fedora one. 


you need a bootloader/grub--you should have installed it to the ubuntu / (sda5).

The easiest way to fix this would be to just reinstall.  At step 7 'Ready to install' hit Advanced button and change the grub location to (hd0,4) or /dev/sda5

(you can backup /var/cache/apt/archives to fedora partition so you don't have to re-download the updates)

unless you want to chroot into it from the live cd, but it might end up taking longer

---

### Post by doobiest on 2008-12-16
They way you have 'ubuntu' set up in there is they way you'd do windows. So, ya.  Linux is linux so just like Fedora has the kernel specified you need to specify what kernel to load with ubuntu. 

It would be something like this.

title Fedora (2.6.27.7-134.fc10.i686)
	root (hd0,0)
	kernel /vmlinuz-2.6.27.7-134.fc10.i686 ro root=UUID=37defdf4-3131-4234-8860-172bc611af55 rhgb quiet
	initrd /initrd-2.6.27.7-134.fc10.i686.img
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,0)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=37defdf4-3131-4234-8860-172bc611af55 rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img
title Ubuntu
	root (hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet



The initrd and vmlinuz part all depends on what kernel you have.  The easiest way would be to boot into redhat. Mount /dev/sda5 to something like /media/temp and then browse to /media/temp/boot and get the exact name for the initrd and vmlinuz file

---

### Post by logos34 on 2008-12-16
> **doobiest said:**
> 
The initrd and vmlinuz part all depends on what kernel you have.  The easiest way would be to boot into redhat. Mount /dev/sda5 to something like /media/temp and then browse to /media/temp/boot and get the exact name for the initrd and vmlinuz file

Doobiest,

the problem is that the OP didn't install grub...The entry

> title Ubuntu
	rootnoverify (hd0,4)
	chainloader +1

is a 'chainloader' entry, and would normally work, but grub needs to be written to the bootsector of the ubuntu / (sda5) first, and to do that there needs to be /boot/grub/ files...Running grub-install won't work unless you're booted into the system in question or chrooted into it via live cd.

---

### Post by doobiest on 2008-12-16
WHAT? no....

Grub doesn't need to be installed on sda5. 

Here are the requirements.  

1) Grub is installed on the MBR of any drive, so that upon booting that drive it takes you to the grub splash screen
2) The OS you're trying to boot has a /boot directory containing vmlinuz and initrd

and that's pretty much it.

3) Tell grub that you want to read hd0,4 and load the vmlinuz/initrd files from /boot on hd0,4.


There's no good reason why would can't use a version of grub installed by a different distro to boot into Ubuntu.  If that weren't the case how would you expect to be able to use ubuntu's version of grub to boot back into Fedora?

The only problem here is that ge has an existing grub that was installed by Fedora which is referencing a menu.lst file which doesn't include the proper information to load Ubuntu.

For an second option, which would be to installed ubuntu's version of grub, chrooting isn't required.  Also you have to do it load up the live CD and issue this:

#grub

     grub> root (hd0,4)
     grub> find /boot/grub/stage1
     grub> setup (hd0)


Now this will work assuming the even though he didnt install the ubuntu version of grub /boot/grub on sda5 still exists which it might not. 

If /boot/grub exists the first problem he will have is he now replace'd a fedora version which is absent of ubuntu's info, with an ubuntu version which is absent of fedora's info. So no matter what way he goes about it he has to put one or the other distro's info into a menu.lst.

I would suggest deciding what is your primary distro, fedora or ubuntu, and if it's still fedora I would go with my initial recommendation. If it's going to be ubuntu I would go with my second suggestion.

Essentially i'm saying A) modify Fedora's existing menu.lst or B) create a new menu.lst on the ubuntu partition and use that.

---

### Post by logos34 on 2008-12-16
well, actually there is the **[direct kernel boot method]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.")** (doesn't require menu.lst or grub stage1 installed), which Het Irv could try first.  Basically hit c for commmand line in fedora grub screen, then

> grub>  root (hd0,4)
grub>  kernel /vmlinuz root=/dev/hda5 (grub will probably see sda5 as hda5)
grub>  kernel /vmlinuz root=/dev/hda5
grub>  initrd /initrd.img
grub>  boot_


---

### Post by doobiest on 2008-12-16
Ya that's fine and all I'm just saying he had to make a easy change to his existing grub config to get it to work.

---

### Post by logos34 on 2008-12-16
> **doobiest said:**
> Ya that's fine and all I'm just saying he had to make a easy change to his existing grub config to get it to work.

ok, I see what you're saying...I missed this part of your post:

> title Ubuntu
root (hd0,4)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

yes that should work

But this would not:

> grub> root (hd0,4)
grub> find /boot/grub/stage1
grub> setup (hd0)

since there's no ubuntu /boot/grub folder (which is where stage1, menu.lst etc are stored)--when you elect not to install the grub bootloader, it doesn't make a /grub folder with those files

---

### Post by doobiest on 2008-12-16
Ya I agree, I did mention that it likely wouldnt work because those files probably aren't there. I wouldn't know though because I've never opted out of installing grub.

---

### Post by Zombie2 on 2008-12-17
Hi
I was using 8.04 and Xp. Reinstalling Xp erased the bootloader.

Now in rescue mode (ubuntu), i cant reinstall grub. Even, trying 'manual partition' to set mount point is not working. It shows no existing partition. BUT, fdisk showing all partitions. AND, from a shell, i can see /boot/grub/menu.lst 

At this point, how can i reinstall grub from this shell (rescue mode) to MBR?? help plz !!!

Note: considering no "grub>" prompt

---

### Post by Het Irv on 2008-12-17
Sorry for going AFK on this thread, but I only have web access at work... and I wasn't going to stay here just for this.


```
grub> root (hd0,4)
grub> find /boot/grub/stage1
grub> setup (hd0) 

```

That didn't work, just to let you know, so you are right on that.  But I did try using the intird & vmlinuz files like you suggested, but I used UUID instead of /dev/sda5.  And the screen started to fade to white on the edges during boot.  Sorta like if you were to take a can of air and spray it upside down on something.  In bit I will try using /dev/sda5 and see if that makes a difference.

---

### Post by doobiest on 2008-12-17
haha that's wild, why did you use the UUID?  Personally I dont like them because they aren't very human readable so I like to assign it by device.  I haven't really researched them much but I think the main reason to use them is so if your drives change order you don't get issues like /dev/sda changing to /dev/sdb, but I never swap drives or anything so I don't have that problem.

For the sake of getting it running you should go with my suggestion and do /dev/... to rule out human error.

---

### Post by doobiest on 2008-12-17
> **Zombie2 said:**
> Hi
I was using 8.04 and Xp. Reinstalling Xp erased the bootloader.

Now in rescue mode (ubuntu), i cant reinstall grub. Even, trying 'manual partition' to set mount point is not working. It shows no existing partition. BUT, fdisk showing all partitions. AND, from a shell, i can see /boot/grub/menu.lst 

At this point, how can i reinstall grub from this shell (rescue mode) to MBR?? help plz !!!

Note: considering no "grub>" prompt

Hey this is easy you have to type grub into a terminal to get into the grub> prompt. From there you can follow the instructions I left above.  Keep in mind that the (hd0) hd(0,4) part is different for everyone.  

ei:  HD(X,Y)

X= the drive number, so if it's the first drive (/dev/sda) Then that's 0
Y= the partition number that contains /boot/grub/  so if it's the first patition (/dev/sda1) then that's also 0.

---

### Post by Het Irv on 2008-12-17
Alright! its working! 

I did two things not sure which got it working but I will lay them both out for you:

1. First I pulled Ubuntu from the extended drive and gave it, its own primary partition. Now Ubuntu is installed on /dev/sda3

2. Then under the advanced options I installed GRUB to sda3.

Then as a last step I pointed Fedora's GRUB entry to (hd0,2).  And it booted straight in, no problems.

Thanks for everyone's help.

---

### Post by doobiest on 2008-12-17
I'm glad it worked but you went though way more work than necessary ;-)

---

### Post by Het Irv on 2008-12-17
Its called the learning process. If I get the time I might write up a: 
HOW-TO: Installing Ubuntu beside another OS w/out overwriting MBR.

So that I can find it next time I forget.

---

### Post by doobiest on 2008-12-17
No I mean the way you did it was way more work than what I was trying to get you to do.

And the title of that how-to is not what actually happened.

Additionally just FYI in case you didn't know. If you chose to install grub initially during the install process it would have worked fine and maintained your Fedora boot information.

---

