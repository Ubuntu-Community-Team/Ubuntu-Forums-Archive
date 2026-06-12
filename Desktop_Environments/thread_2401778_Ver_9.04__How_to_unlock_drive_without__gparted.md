---
title: "Ver 9.04 | How to unlock drive without  gparted?"
date: 2018-09-22
forum: Desktop Environments
---

### Post by a-bell on 2018-09-22
Hi
I have an old laptop with Xubuntu 9.04 installed, the HDD where Xubuntu is installed is locked, How do I unlock it? (I can boot Xubuntu)
The objective is unlocking the HDD and erasing everything on it.
I tried running another distro installed on a CD but the gparted (of that other distro) couldn't do anything because of the locked HDD.
I tried to use the gparted live DVD but regardless of the mode I chose, the gparted wouldn't load.

This computer (AKA Xubuntu OS) doesn't have gparted installed and trying to install it using the "sudo apt-get update" or "sudo apt-get install gparted" only gives me errors, even when connected to the internet router (by LAN cable (RJ-45)).

---

### Post by TheFu on 2018-09-22
9.04 support ended in early 2010.  It is against forum policy to help with unsupported releases.

In-use partitions cannot be modified.  If you boot from the partition, then it will always be "in-use."

However, you can download and make a live-boot flash or DVD/CD with 16.04 or 18.04, both are LTS releases and have 5 yrs of support from their April release date by the year. Then boot from the boot media you just made and you can wipe the entire HDD/SSD disk and install a fresh release.

From the flash boot, you can install **gparted** or use overwrite the disk using **dd**.

---

### Post by yancek on 2018-09-22
When you say the drive is "locked" are you referring to the lock icon in GParted?  If so, that is there to indicate the partition(s) are mounted so you need to unmount them which you can do by following the instructions in the post above.

---

### Post by a-bell on 2018-09-22
Yes, the "locked icon", when I try to unmount it using another distro it says "umount: can't umount /initrd/mnt/dev_ro2: Device or resource busy".


@TheFu "[COLOR=#000000] live-boot flash or DVD/CD with 16.04 or 18.04"[/COLOR] unfortunately the computer I'm trying to revive is a Fujitsu lifebook s4546, it's RAM it's not much more than 200MB.

I'm sorry if it is against policy to help with an unsupported release, but if a release is unsupported it should have at least a guide on how to upgrade or remove the OS.

---

### Post by Frogs Hair on 2018-09-22
There is no upgrade path for a release that old because all the releases in between 9.04 and current supported releases have reached end of life. There's not likely any forum volunteers that could provide informed support for 9.04.

---

### Post by Frogs Hair on 2018-09-22
[DBAN]("https://sourceforge.net/projects/dban/") is an option for wiping the drive tough you have to make a bootable USB or CD. I see no specific instructions for use.

---

### Post by TheFu on 2018-09-22
> **a-bell said:**
>  @TheFu "[COLOR=#000000] live-boot flash or DVD/CD with 16.04 or 18.04"[/COLOR] unfortunately the computer I'm trying to revive is a Fujitsu lifebook s4546, it's RAM it's not much more than 200MB.

I'm sorry if it is against policy to help with an unsupported release, but if a release is unsupported it should have at least a guide on how to upgrade or remove the OS.

Those guides existed in 2010.  It is 2018 now.  Canonical does a good job of removing crufty old guides so they don't show up in web searches.  But the upgrade path from 9.04 to anything currently support never existed and certainly wasn't known in 2010.

There are probably many, many ways to solve this issue.  I provided 1.  The **dd** program running from some alternate boot media can wipe any storage, assuming the drivers for it still work.  A distro like tinycore will run on that little RAM, but there's no way to know specifically if it will run on that model. I doubt any modern variant of Ubuntu with a GUI will run at all on it, but I'm guessing based on the tiny amount of RAM.  Most i386 distros removed support for CPUs that aren't at least i686 years ago. Google says it has a Pentium3 CPU.  Ouch.  A $35 Raspberry Pi v3+ would be faster and has more RAM.

---

### Post by a-bell on 2018-09-22
Nice, either dd or DBAN will erase the disk, I'll try both!

Thanks for your answers, I will post again if it worked or not.

---

### Post by a-bell on 2018-09-27
Update:
The drive got erased and everything is good now.

---

