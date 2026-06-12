---
title: "Ubuntu 6 screws up Vista boot - GRUB problem"
date: 2006-07-07
forum: Desktop Environments
---

### Post by beckyh on 2006-07-07
I have a problem here that I hope you can help me with.
I am currently Ubuntu-less due to having a hissy fit at my laptop.

Dual booting windows XP and Vista public beta.  I had all the partitions sorted and ready to put Ubuntu back on. XP goes on first, then Vista and finally Ubuntu.  Setup went perfectly but GRUB screws up my Vista and I cannot boot into Vista - I get error - failed to find winload.exe

When I installed mandrake alongside XP and vista, vista booted fine.  But this grub does not seem to like it and obviously does something to this winload.exe file.  Not really sure where to start on this one.  Because Mandrake did not screw up the boot I am certain this is a grub problem.

Has anyone had a similar experience with this please?

---

### Post by llamakc on 2006-07-07
I don't have an answer but I know that the person who does will probably like a looksee at your /boot/grub/menu.lst file. Please post its contents.

---

### Post by beckyh on 2006-07-07
Thankyou for the quick reply.  I don't actually have Ubuntu installed at the moment as I needed to get Vista back and I screwed everything up and lost it. Will likely do it again tomorrow. 
Is it possible to install Ubuntu without Grub and use the windows bootloader? With Ubuntu 5 I am sure I was able to choose whether or not to install grub, but I dont recall version 6 giving me that option.

---

### Post by Iarwain ben-adar on 2006-07-07
Hi, 
i don't have an answer as well,
but i do now this:
Windows can't (or doesn't want to :D ) accept linux in it's loader.

And yes, DD still asks you if you'd like to install GRUB :D


Iarwain

---

### Post by beckyh on 2006-07-08
Right I have now installed Ubuntu 6 to try and replicate the problem and the problem is still there but also my grub is very messy.

I have the following operating systems listed in grub

Ubuntu, kernel 2.6.15-23-386
Ubuntu, kernel 2.6.15-23-386 (recovery mode)
Ubuntu, memtest86+

Other operating systems
Windows NT/2000/XP (this is not an OS but a built in recovery partition)
Microsoft Windows XP Home Edition 

By selecting the last XP one, this takes me to a new boot menu offering either earlier windows (xp) or microsoft windows (vista).  Vista fails to load with missing winload.exe file.

So what I have done is booted with the Vista dvd and have done a repair, it detected the boot problem and fixed it.  So now on the second menu I have the above entries plus a new one "vista ultimate recovered".  This one does actually boot.

So while I can now boot to either ubuntu, xp or vista, my boot menus are very messy as you can see. 
What I really need is ubuntu, ubuntu recovery, the second XP entry and the vista entry all on one menu. Is this possible please?

---

### Post by Iarwain ben-adar on 2006-07-08
Shure 't is possible,
please post your menu.lst ;)


Iarwain

---

### Post by beckyh on 2006-07-08
Sorry its long.  I have not included all the generic default text at the top and have only included the important stuff.

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
.............................

End paste. As you can see it does not show the vista versions. I have a feeling they may not be able to be added to grub as I can only get to the via the last XP entry with a new menu.  Its not a problem if it cannot be changed but I would like to simply the menu as much as possible. 
Thanks for your help.

---

### Post by Iarwain ben-adar on 2006-07-08
> **beckyh said:**
> 
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
[COLOR="Red"]#[/COLOR]title		Other operating systems:
[COLOR="Red"]#[/COLOR]root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
[COLOR="Red"]#[/COLOR]title		Windows NT/2000/XP
[COLOR="Red"]#[/COLOR]root		(hd0,0)
[COLOR="Red"]#[/COLOR]savedefault
[COLOR="Red"]#[/COLOR]makeactive
[COLOR="Red"]#[/COLOR]chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1



This is how i should do it. Unfortunately, The Vista boot won't be included (it can, but i don't know how :D )

NOTE: I did not exclude memtest 86+ (don't know what purpose it has, but anyways... If you'd like to exclude it aswell, simply put # in front of the line :D


Iarwain

---

### Post by beckyh on 2006-07-08
> **Iarwain ben-adar said:**
> This is how i should do it. Unfortunately, The Vista boot won't be included (it can, but i don't know how :D )

NOTE: I did not exclude memtest 86+ (don't know what purpose it has, but anyways... If you'd like to exclude it aswell, simply put # in front of the line :D


Iarwain

Thankyou Iarwain.

I will not include this one
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
#title Windows NT/2000/XP
#root (hd0,0)
#savedefault
#makeactive
#chainloader +1

As that is just an XP restore partition that I will never use.  
Why did you put some in red?  Is that relevant at all?  Just that I am fairly new to linux so don't know if its important.  Sorry if its a rubbish question.  lol

---

### Post by Iarwain ben-adar on 2006-07-08
The ones in red are the things i changed ;)
Makes it easier to see the difference :D


Iarwain

---

### Post by beckyh on 2006-07-08
> **Iarwain ben-adar said:**
> The ones in red are the things i changed ;)
Makes it easier to see the difference :D


Iarwain

I get ya.  I didn't realise the hashes # meant exclusions.  
I am getting there slowly, thankyou very much for the help

---

### Post by Iarwain ben-adar on 2006-07-09
No problem,
i'm learning aswell :D


Iarwain

---

