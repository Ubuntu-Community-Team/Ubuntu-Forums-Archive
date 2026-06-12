---
title: "iso help"
date: 2015-07-13
forum: Development CD/DVD Image Testing
---

### Post by Tim_Trimble on 2015-07-13
First, I have to admit I am new to this part of Ubuntu.  I downloaded and installed Ubuntu 12.10, then upgraded it to current.  I then added a lot of add-ons and configured the machine to run apache-openmeetings 3.  All is now working, the problem is I would like to create a disk image so I can share my work.  The iso needs to be a complete copy of the entire os and it needs to be bootable so it can be installed on a blank box.  A good example of what I want to end up with would be the iso's offered for FreePBX, Elastix and TrixBox.  They are program iso's that include the entire os already configured to the special needs of the software it will run.

If anyone can direct me to the info I need to complete this, I would appreciate it.

---

### Post by Dreamer Fithp Apprentice on 2015-07-14
Get remastersys. There are 2 forks at sourceforge. I've used one of them successfully with 14.04. Offhand I forget which one and I can't check because that was on a desktop that is broken at the moment. Use the "backup" option and you get a live disk that is a functional copy of your system and can also be used to install a copy to another machine.

---

### Post by coldraven on 2015-07-14
> I downloaded and installed Ubuntu 12.10, then upgraded it to current
I don't know why you did that, I find that the upgrade method is sometimes problematic. In the future just get the latest Long Term Support (LTS) version directly and do a fresh install.
All versions can be found here, I use the torrent download option because it's very fast. To see the torrent option click on 14.04.2 then scroll down the page a bit.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Also maybe Clonezilla might be useful, the destination drive must be at least as big as the original.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Dreamer Fithp Apprentice on 2015-07-14
Clonezilla is pretty good too. If ALL OP wants to do with the resulting removable media is install a copy of his system to another hard drive, it should work also. I'm not sure it is as robust as Remastersys. I may be wrong, but I believe it uses either of several partition cloning programs (like dd for example) whereas Remastersys uses the regular Ubuntu installer, Ubiquity. So if he isn't installing back to identical hardware, he may be more likely to have problems with innappropriate drivers and config files with Clonezilla.

Also> **Tim_Trimble said:**
>   The iso needs to be a complete copy of the entire os and it needs to be bootablesounds to me like he wants a bootable copy of his system on live media. Clonezilla doesn't do that unless they've added that feature since I've used it. The Clonezilla disk ITSELF is bootable, but it doesn't contain any features the Clonezilla devs didn't put there. So for instance if the OS being cloned uses giant fonts or text to speech  those features won't be there when you boot Clonezilla. All your tweaks are stored in the IMAGE file that Clonezilla produces of your OS and that file is NOT bootable, nor is a CD or thumb drive made from it - it's just a data file containing a complete description of the partitions copied - and those features will only be available after you use Clonezilla to restore the image to (a/some) hard drive partition(s) and boot the resulting system.

---

### Post by Tim_Trimble on 2015-07-16
> **coldraven said:**
> I don't know why you did that, I find that the upgrade method is sometimes problematic. In the future just get the latest Long Term Support (LTS) version directly and do a fresh install.
All versions can be found here, I use the torrent download option because it's very fast. To see the torrent option click on 14.04.2 then scroll down the page a bit.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Also maybe Clonezilla might be useful, the destination drive must be at least as big as the original.
[http://clonezilla.org/](http://clonezilla.org/)

I started with 12.10 because the documentation for Openmeetings is so old that ver 12 was as high as it went, but then found out that a lot of update links for 12 are broken now so i did an upgrade.  I asume i could of started with 14 if i would have known.  My desire is to bring Openmeetings back to life, it's a good program, but has no accurate documentation.

---

