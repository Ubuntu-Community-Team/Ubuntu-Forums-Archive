---
title: "Dual Boot With XP"
date: 2005-12-11
forum: General Help
---

### Post by Tmyers on 2005-12-11
Ive installed Ubuntu on an older Gateway and in the last few days have grown to like it alot. I want it on my newer pc but still would like to keep windows for at least a little while, for gaming and such. I have read up on dual booting and am pretty confident in my ability to do so, but I have just one question. What are the minimum system specs for a dual-booting system? I dont want to install a second OS and not be able to do anything on it because of slow loading, etc. Your help would be appreciated.

---

### Post by taurus on 2005-12-11
There is NO minimum system spec for dual boot!  If you want to run both XP (or windows) and Ubuntu (or Linux) on the same machine, install windows and and then Ubuntu last.  And when you get to the section about bootloader, have it install GRUB on MBR.  GRUB is smart enough to add an entry for your windows so you can choose whichever OS you want to boot when you turn on your machine...

---

### Post by eXSBass on 2005-12-11
Okay, their's no set minimum value for Dual Booting however I recommend when doing so make sure you make a partition for all your work or anything else that you'll need accessing from Ubuntu and Windows. Make the partition readable by the two, so you don't need to switch between OS's. NTFS I think is right.

I wouldn't recommend dual booting with less than 20Gb. Even if you have 20Gb I still reckon that's hell of alot less. I really recommend 40Gb and above, but 20Gb should suffix for the beginners like me and you. However I do have a 160Gb HDD.

Just make sure YOU READ EVERYTHING WHEN PARTITIONING AND INSTALLING SO YOU DO NOT WIPE YOUR WINDOWS PARTITION OR ANY OTHER DATA THAT YOU MIGHT NEED!

But in short, its really easy.


Edit: If theirs anything you don't understand abort installation and report back. I had problems when dual booting Ubuntu and Windows. Just give me a shout if you need help.

---

### Post by linbetwin on 2005-12-11
If XP works on that computer, Ubuntu should work too. The only thing you need is at least 3 GB of hard disk space. You're not going to run both XP and Ubuntu at the same time and neither system is going to be affected in any way by the presence of the other on the hard disk.

---

### Post by JoshHendo on 2005-12-11
As long as there is enough room on the HDD for both, it is VERY easy to install. Also, you can learn from my mistake, never install it on a slave HDD (you can't boot off that, so I got a error in grub. All fixed though :)) :P.

---

### Post by aysiu on 2005-12-11
This tutorial will help you set up the dual boot:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Tmyers on 2005-12-11
alright guys, I seem to have enough space so Im going to go ahead and do it tonight when i get home from a chritmas party. Wish me luck :)

*If I have any problems Ill hop on another computer and pm you eXSBass

---

### Post by YanH on 2005-12-11
[QUOTE=eXSBass]Okay, their's no set minimum value for Dual Booting however I recommend when doing so make sure you make a partition for all your work or anything else that you'll need accessing from Ubuntu and Windows. Make the partition readable by the two, so you don't need to switch between OS's. NTFS I think is right.
[/QUOTE]

Ubuntu cannot write to NTFS so if you want to be able to edit theses files within windoze and Ubuntu then you should use FAT32. I think there is also software available which allows windoze to read and write EXT2 and EXT3 files. I've found this Project on Sourceforge which does just this. It's available here at [http://sourceforge.net/projects/ext2fsd]("http://sourceforge.net/projects/ext2fsd").

---

### Post by Tmyers on 2005-12-11
Ive checked and my windows hardrive seems to be using NTFS. If I follow aysiu's link I can choose to partition and install using it's NTFS method. However this is asking that I make 2 more partitions,making a total of 3. Is it wise to have 3 partitions? Would it be easier if I converted the windows hardrive to FAT32? Can I do this without erasing all of my files?

---

### Post by Ocxic on 2005-12-11
[QUOTE=Tmyers]Ive checked and my windows hardrive seems to be using NTFS. If I follow aysiu's link I can choose to partition and install using it's NTFS method. However this is asking that I make 2 more partitions,making a total of 3. Is it wise to have 3 partitions? Would it be easier if I converted the windows hardrive to FAT32? Can I do this without erasing all of my files?[/QUOTE]


Get Partition Magic and resize your NTFS windows partition that way you can keep all of your files, but this is risky, I reccommend you backup anyway just in case something goes wrong, but u should be ok.

---

### Post by Tmyers on 2005-12-11
I honestly dont think I want to mess with the windows partition at the moment, as I am not in the mood for making back-ups (not in the mood meaning no disk handy) . Can I just make a second partition, install ubuntu on that and make the third partition at a later date? (after I have made back-ups and feel more confortable) I dont think it's a neccesity that I need to access windows files on linux at this point, mainly because windows is mostly used for gaming and photoshop and I will probably continue using it for these things for at least a while.

---

### Post by JoshHendo on 2005-12-11
[QUOTE=Ocxic]Get Partition Magic and resize your NTFS windows partition that way you can keep all of your files, but this is risky, I reccommend you backup anyway just in case something goes wrong, but u should be ok.[/QUOTE]

Partition Magic costs $$. Ubuntu has a partitioning tool in the installation.

---

### Post by aysiu on 2005-12-11
[QUOTE=Tmyers]I honestly dont think I want to mess with the windows partition at the moment, as I am not in the mood for making back-ups (not in the mood meaning no disk handy) . Can I just make a second partition, install ubuntu on that and make the third partition at a later date?[/QUOTE] Making the second partition "messes" with your Windows partition by shrinking it. Any repartitioning should always happen after a backup of your most important documents.

---

### Post by Tmyers on 2005-12-11
o alright, I didn't know that making a second partition would shrink my window's one, but now that I think about it I should have know. Windows has the whole computer at the moment. Adding something else would take away from that space. Ill back my stuff up and do this another day.

---

### Post by Tmyers on 2005-12-11
Alright...I hunted..cleared some old disks - backed up and got to installing. I have followed the tutorial at ([http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)) and gotten to step 8th NTFS. In their screenshot they have only 1 partition..the primary. This is what shows under my Partition Disks menu:

#1 Primary 41.1 MB FAT16 media/hda1
#2 Primary 41.1 GB NTFS media/hda2
pri/log         8.2 MB      FREE SPACE


why do I have more than 1 primary. u have never made any other partitions on this computer? Which partition do I shrink down so I can make more? Sorry if Im being a pain but Im a bit new at this. Your guys help is definitely appreciated

---

### Post by Ocxic on 2005-12-11
I have no idea why there is 2, but you want to shrink/resize the second one: hda2

---

### Post by Danielle on 2005-12-11
[QUOTE=Tmyers]Alright...I hunted..cleared some old disks - backed up and got to installing. I have followed the tutorial at ([http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)) and gotten to step 8th NTFS. In their screenshot they have only 1 partition..the primary. This is what shows under my Partition Disks menu:

#1 Primary 41.1 MB FAT16 media/hda1
#2 Primary 41.1 GB NTFS media/hda2
pri/log         8.2 MB      FREE SPACE


why do I have more than 1 primary. u have never made any other partitions on this computer? Which partition do I shrink down so I can make more? Sorry if Im being a pain but Im a bit new at this. Your guys help is definitely appreciated[/QUOTE]
maybe the first partition is from an old version of windows which was on the disc before XP. if that's the case and you only use XP then the first partition isn't being used!

if you are sure XP is running on ntfs and you aren't running an old OS too then the first partition is free.

---

