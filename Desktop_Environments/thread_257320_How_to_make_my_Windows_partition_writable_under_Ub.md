---
title: "How to make my Windows partition writable under Ubuntu?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Physicist on 2006-09-14
How to make my Windows partition writable under Ubuntu?

I would like to have a folder under Windows completely(rwx) shared with Ubuntu, so I can have files in that folder updated sometimes under Windows sometimes under Linux. Thank you.

---

### Post by turbojugend_gr on 2006-09-14
I suggest formatting some unused space under fat32(vfat) so both OSes can write on that, as NTFS write support is poor and experimental. Check this how-to: [https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html)

---

### Post by slibuntu on 2006-09-14
Nope, i'd suggest following this guide by givre, it should do the trick 
[http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by turbojugend_gr on 2006-09-14
Well, it is up to you, but I insist that NTFS write-support is still experimental and risky, that's what the how-to composer says in his first words actually. Also since you only need a folder to make changes into I vcan't see any harm by making that a partition too, that way you won't loose your data over frormats to the system disks. Especially if you plan to use this folder/partition for music/videos etc, you won't bother with backing them up when formatting either ubuntu or winxp for any reason. Again your decision m8.

---

### Post by Physicist on 2006-09-14
> **turbojugend_gr said:**
> Well, it is up to you, but I insist that NTFS write-support is still experimental and risky, that's what the how-to composer says in his first words actually. Also since you only need a folder to make changes into I vcan't see any harm by making that a partition too, that way you won't loose your data over frormats to the system disks. Especially if you plan to use this folder/partition for music/videos etc, you won't bother with backing them up when formatting either ubuntu or winxp for any reason. Again your decision m8.

If my NTFS partition already has a WIndows, what too should I use to take part of this partition and make it as FAT32 without reinstalling this Windows OS?

---

### Post by turbojugend_gr on 2006-09-14
The safest way i prefer is through WINDOZ, lol I know it sounds rediculus, but my view oin that is it can't break up itself! Pretty tough point don't you thing? SO iwould boot up into those bloody windoz and go for the disk manager tool (right click on my computer it's about the middle of the list). I 'd open it and then:

> I would pick my windows drive and ask the disk manager to create a partition under it, it will manage the free space by itself, remember to make it fat32 format. Notice you can't make a fat partition bigger than 32gigs due to gate's companies diabilities (If you desire a bigger partition I will give you a link with a third-party program that manages bigger fat partitions-so ask for it). It should do the job (surpringly).

> Then I would boot into ubuntu, and go edit /etc/fstab file so as to make this new partiotion mounted read/write on boot up too. (if you wish help on that go for [this]("https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html") page it is a very easy task to perform.

then ```
mount -a
``` in a terminal and here you are, your desire is fulfilled. Let me know how it goes m8.

---

### Post by turbojugend_gr on 2006-09-14
Also going through windoz to make that partition will ensure it is usable and 100% working under it, as I had some case in the past, in which I had to make it recognize it, not easy since we talk about fool's OS here... So go for it it should work like a charm! ;)

---

### Post by X.Cyclop on 2006-09-14
I never had a problem with **ntfs-3g** or my NTFS partitions, so don't worry.;)

---

