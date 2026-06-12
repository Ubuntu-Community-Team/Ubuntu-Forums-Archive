---
title: "The &quot;Feisty broke my Vista&quot; thread"
date: 2007-07-11
forum: Desktop Environments
---

### Post by adamz70 on 2007-07-11
Hi all, I just wanted to put a cautionary word out there for Vista users (in the shape of a desperate plea)!

I bought a new Asus A8JS notebook after reading in these forums that it runs Ubuntu just fine. However, I was unable to avoid one loaded with Vista Business. I just attempted to install Feisty (Studio), while keeping Vista for gaming using the boot DVD.

What resulted was a working version of Ubuntu Studio. I then logged out and back into Vista which gave me a massive "ERROR" screen, including the message "Could not open file c:/recovery.dat"

I restarted to find GRUB now broken, giving me Error 17, followed by Error 22 on subsequent reboots.

I tried using my (Asus) Vista recovery disks which seem to have wiped Feisty, but not GRUB. I'm left with a broken GRUB, and no way of booting into Vista to fix my Master Boot Record. I have gone into Ubuntu via a live CD and tried to remove GRUB which has done nothing.

I wanted to put this on the forum because my searches have found nothing, and therefore it could be a new problem.  Please help!!! Thanks in advance!

---

### Post by tcpip4lyfe on 2007-07-11
Might have to start over.

[http://ubuntuforums.org/showthread.php?t=207870](http://ubuntuforums.org/showthread.php?t=207870)

Vista + ubuntu Dual boot.

Good luck mate.

---

### Post by andrewsomething on 2007-07-11
I'm not sure what advise to give beside just starting clean. But it is possible. I'm dong it right now with Feisty and Vista Home Premium. I found that the easiest way to do it is to install Vista first and then use either Vista's drive management program or the GParted live CD to shrink the Vista partition to the size you want. Next install Fiesty using the option to install in the largest unused space. 

If you search there are a number of good tutorials out there...

Good luck!

---

### Post by adamz70 on 2007-07-12
Thanks guys. My main problem is that the Vista recovery discs supplied by ASUS are *crap* - they don't have any kind of MBR recovery utility, and so the MBR partition (containing GRUB presumably) just stays there no matter how many times I reinstall Vista.

Luckily I have some old XP disks laying around which should let me remove all partitions and format the disk. I'll then use my Vista disks, and THEN use this tutorial to dual boot *properly* with Feisty. (I suppose I could use the Ubuntu Live disk to do this as well?)

[The definitive dual-booting guide: Linux, Vista and XP step-by-step:]("http://apcmag.com/node/5162/")

I guess this isn't the ideal fix (as not everybody has XP disks), but I recommend that any Vista users read the dual-booting guide, as - unlike XP - it's not just a matter of using the Live CD to install Ubuntu alongside Windows any more!! (Possibly a matter for future Ubuntu releases?)

I'll report back if anything else comes up. Thanks again guys.



A

---

### Post by Ni85 on 2007-12-19
Hey guys..
i have the same problem, again with an asus, but i don't have xp disks to save me.. what should i do?
vista was working, then i correctly installed ubuntu 7.10 and vista stopped working with the message "Can not open file C:\RECOVERY.DAT." and a huge red error message appeared on the screen. i can recover vista only if i delete ubuntu and grub.
how can i install ubuntu without compromising Vista?

thanks for your help

(by the way... total newbie writing)

---

### Post by chestnut1969 on 2007-12-19
Hi All

You have to be exceedingly careful when setting up dual boot. For Vista, there is a utility that comes with it for resizing the Vista partition to allow space for a dual boot.

[http://www.bleepingcomputer.com/tutorials/tutorial133.html](http://www.bleepingcomputer.com/tutorials/tutorial133.html)

You can then allocate this space to Ubuntu when you go through the install i.e. from the live Ubuntu CD. I would personally use the custom disk partition, using the remaining 3x of the 4x primary partitions that are allowed

Partition 1 - Vista
Partition 2 - Linux /
Partition 3 - Linux /home
Partition 4 - Linux Swap

It all depends on your disk size etc, and the desired set up. If you used any more than the 4 available primary partitions, you will need to set up extended partitions.

When in Vista, you can use EasyBCD to restore the MBR to its original state 
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Sooner or later you may be posting a thread 'Vista broke my mind!' :) I ended up downgrading to XP in a VirtualBox setup for the apps that I need for work that are not available under Linux.

If you play Windows games, your situation is different (although Cedega may suffice) [http://www.transgaming.com/](http://www.transgaming.com/)

Cheers

---

### Post by Ni85 on 2007-12-21
hey
first of all thanks
I followed the tutorial but it didn't work again..
I have also tried with this one [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

it allows me to boot into vista but this time i get this on my screen when i try to boot into ubuntu:

GRUB4DOS 0.4.3 2007-06-14 , Memory: 639K / 2046M, CodeEnd: 0x3EF2C
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]

grub>


it seems like vista crashes (in the way descripted above) if i install ubuntu with grub, but ubuntu doesn't work if i don't install it...
any more suggestions?

thanks

---

### Post by apothecaryaaron on 2007-12-22
> **adamz70 said:**
> 
[The definitive dual-booting guide: Linux, Vista and XP step-by-step:]("http://apcmag.com/node/5162/")

 
> **Ni85 said:**
> hey
first of all thanks
I followed the tutorial but it didn't work again..
I have also tried with this one [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
 
it allows me to boot into vista but this time i get this on my screen when i try to boot into ubuntu:
 
GRUB4DOS 0.4.3 2007-06-14 , Memory: 639K / 2046M, CodeEnd: 0x3EF2C
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]
 
grub>
 
 
it seems like vista crashes (in the way descripted above) if i install ubuntu with grub, but ubuntu doesn't work if i don't install it...
any more suggestions?
 
thanks
 
I used a similar method as the guide in the link I quoted from adamz70. I did use the Manual setting instead of Guided when making partitions, but that is because I set up a share between Vista and Ubuntu 7.10.
 
Don't give up! It will work, it just might take a couple of tries. Vista went in one go for me, but dual-boot XP on a triple HDD system gave me nightmares. If you are just learning Linux, or require Windows for some reason, it's worth the effort.

---

### Post by Ni85 on 2007-12-22
i made it!
it was grub creating problems in booting vista. i had to use this: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
as a different bootloader installed directly on vista, free some space using the vista partition manager tool, then install ubuntu writing grub not on the MBR but in the same partition where the new OS was being installed.
so that now i have 2 bootloaders: after the choice given by easybcd if i chose linux i would enter grub again to choose again. for some reasons while in grub it doesn't allow me to boot vista (it stops with the previous error), but i guess i just have to set the grub timing so my actual choice is made on easybcd which seems now to work and boot in both OS's.
it took me 5 days, now let's hope it was worthed! :)
thanks everybody for your help!

---

