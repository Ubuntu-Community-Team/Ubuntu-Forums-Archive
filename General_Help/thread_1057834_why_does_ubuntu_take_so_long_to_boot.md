---
title: "why does ubuntu take so long to boot?"
date: 2009-02-02
forum: General Help
---

### Post by dazift on 2009-02-02
After installing ubuntu ibex through wubi on a compaq presario c700 with vista i found that the average ubuntu boot time is much longer than other installs. the boot slows when it mounts the swap file. its not a big problem but it would be nice to have a faster startup.

---

### Post by endrit10 on 2009-02-02
Because you are using wubi.
Installing on a seperate partition increases boot time.

Still, both XP and Vista boot faster than Ubuntu anyday.
Its because of GRUB, i ******* HATE grub, it is one of the worst pieces of code i have ever had the unfortunate misery of using. GRUB is the culprit to nearly ever ubuntu install ******* up.
If ubuntu is going to move forward, these three things need to happen:

1) Make it more automated, I hate terminal, why can't everything just install itself like exe?

2) Get rid of GRUB. No explanation needed here.

3) Improve the partitioner, I have no idea why GParted cannot see any of my harddrives as NTFS, it thinks they are EXT3 even when no ubuntu is present! It is also a nightmare to use, I have not been able to use Ubuntu on my main pc (this one) because of the partioner whiping my whole harddrive. It is garbageware.

---

### Post by ajgreeny on 2009-02-02
> **endrit10 said:**
> Because you are using wubi.
Installing on a seperate partition increases boot time.

Still, both XP and Vista boot faster than Ubuntu anyday.
Its because of GRUB, i ******* HATE grub, it is one of the worst pieces of code i have ever had the unfortunate misery of using. GRUB is the culprit to nearly ever ubuntu install ******* up.
If ubuntu is going to move forward, these three things need to happen:

1) Make it more automated, I hate terminal, why can't everything just install itself like exe?

2) Get rid of GRUB. No explanation needed here.

3) Improve the partitioner, I have no idea why GParted cannot see any of my harddrives as NTFS, it thinks they are EXT3 even when no ubuntu is present! It is also a nightmare to use, I have not been able to use Ubuntu on my main pc (this one) because of the partioner whiping my whole harddrive. It is garbageware.
Sorry you feel that way, but I think you are probably in the minority.  ubuntu boots faster on my machine than Windows XP by quite a margin, and it also does not keep chuntering away loading the anti- virus program and then zone-alarm, etc etc, in the background, as windows does, and which on my machine can take a long time after the desktop appears.  During this time I find that windows is still impossible to use, and only crawls along.

Gparted is, in my opinion, one of the best partitioning applications there is, and it is normally very good at "seeing" any disk thrown at it.  I feel there must be something very unusual going on with your setup, if it can not see your disks as ntfs, as it has always seen mine and has also on any computer I have used it on.

What exactly is your problem with grub?  I have used it on many machines and it is one of the most configurable and useful boot-loaders around in my experience.  If you want to use windows and linux, you will have to accept that there is a need for something different to the standard windows bootloaders which come with windows.  If you have a separate /boot partition you can even use grub without linux installed on your machine to boot windows only.

Why get rid of terminal?  You may not like it or want to use it, but it can make life a great deal easier occasionally when something goes wrong, and for many people there is generally absolutely no need to use it.  However, there is no reason to abandon it totally fot those of us who do like it and use it.

Please don't assume that because you have had a bad experience, everyone else has, or that the systems that most other people use are also slow and have caused them major problems.  I think you may just be unlucky and have hardware that does not suit ubuntu, or perhaps other linux distros either.

---

### Post by DerHesse on 2009-02-02
GRUB is definetly the best bootloader ever. It can even handle MS-Windows.
 
To use gparted with Ntfs you need to install ntfssupport fpr gparted. (->synaptic will help)
:popcorn:

---

### Post by brainac0cult on 2009-02-02
never diss the grub

---

### Post by brandon88tube on 2009-02-02
Yeah, Ubuntu boots faster for me then XP and I am using wubi. It might be due to the antivirus program that autostarts with XP, but either way its still faster for me. If it takes forever for you maybe you have a lot of programs running on startup.

---

### Post by endrit10 on 2009-02-03
I actually wouldn't really know.
I haven't used XP since 2005.

Don't get me wrong, I don't hate Ubuntu or anything, but Vista and ESPECIALLY windows 7 does boot up faster for me.

Maybe its just my sweet setup:

Intel 965 Core i7 Extreme 3.20GHz
3GB DDR3 RAM
GeForce GTX 295
64-Bit Windows 7 

All I can say is, it rapes Windows 7, Win7 boots in 14 seconds.
Oh an I have a minimalistc installation of windows, no themes , tweaked for max performance etc.


@DerHesse

I didn't know that!
I will try again.

---

### Post by dazift on 2009-02-03
thanks you guys but no one has given me a solution to my problem.

even though ubuntu takes forever to start, vista takes a bit longer. the average time for an ubuntu boot is supposed to be somewhere in the 30 sec range. myn is well over 1 min. and it has nothing to do with how many start up programs i have, as i mentioned the thing that slows down the process is the time it takes to mount the swap file. I know that this has something to do with wubi and i was writing this thread to see if someone has a fix or if they are experiencing the same problems.
i dont care about your opinions of grub i just want a faster start up time, especially since us wubi ppl cant hibernate. thanks

---

