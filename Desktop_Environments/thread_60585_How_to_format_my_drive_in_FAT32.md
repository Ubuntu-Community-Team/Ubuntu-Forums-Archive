---
title: "How to format my drive in FAT32?"
date: 2005-08-28
forum: Desktop Environments
---

### Post by veraction on 2005-08-28
nt

---

### Post by arnieboy on 2005-08-28
[QUOTE=veraction]OK, I want to format my 180GB drive for use with Ubuntu/Windows. I've done it before, but I forgot how I did it exactly and everything I try isn't working

I've tried booting with Ubuntu 5.04 Install CD then when it comes to partitioning, I do manually partition, then select the 180GB for FAT32 partition (with plans of exiting/rebooting once its formatted). However it gives me an error saying that it failed.

The drive is: /dev/hdf

I tried this, but get error. ```
fdisk hdf
Unable to open hdf
``` 

I tried installing Partition Magic 8.0 and 7.0 Demos in windows but it crashed every time I tried to open it.

Is there any program I can install in ubuntu which will help?

or anyone know why fdisk isn't working? syntax error?

[edit] also tried cfdisk, but got error saying it couldn't open drive
[edit2] also cannot format it as fat32 in winXP since it is > ~30 GB[/QUOTE]
first do a *sudo fdisk -l* to make sure ur drive indeed is */dev/hdf*. 
then do *sudo fdisk /dev/hdf * and look in the menus to find the "format a partition" tool.
Once that is done (set the new format to reiserfs), run:
*sudo mkfs.reiserfs /dev/hdf*
now mount it and enjoy.
u might get mounting errors if u try to partition it as a fat32 by doing a "mkfs.vfat".

---

### Post by veraction on 2005-08-28
ah ok. very stupid mistake. wasn't using sudo -- though i wish it would've given me a more helpful error message

---

### Post by veraction on 2005-08-28
well I did what you said but it didn't work. fdisk worked fine, but that weird program didn't make it so Windows could read/write to it (as FAT32)

I used cfdisk to format as Win FAT32, but my WinXP couldn't read/write to it.

this is really starting to piss me off

---

### Post by manicka on 2005-08-28
You could try using Gparted (it's in universe) which is similar to partitionmagic

---

### Post by veraction on 2005-08-28
gparted sounds good.

```
~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gparted
```

when using clean install of ubuntu

guess i'll have to figure out some sites to add to my /etc/apt/sources.list

---

### Post by manicka on 2005-08-28
[QUOTE=veraction]gparted sounds good.

```
~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gparted
```

when using clean install of ubuntu

guess i'll have to figure out some sites to add to my /etc/apt/sources.list[/QUOTE]
 you can add these easily in synaptic

Settings --> Repositories. Click on the add button

---

### Post by veraction on 2005-08-28
ok, i did that ^ then installed gparted & formatted the drive as FAT32..

but Windows still doesn't recognize it. Computer Management says its FAT32 (Unknown partition) & I can't assign it a drive letter.

No wonder why so little people use linux  :cry:

---

### Post by manicka on 2005-08-28
[QUOTE=veraction]ok, i did that ^ then installed gparted & formatted the drive as FAT32..

but Windows still doesn't recognize it. Computer Management says its FAT32 (Unknown partition) & I can't assign it a drive letter.

No wonder why so little people use linux  :cry:[/QUOTE]
 Let me get this right. You couldn't do this job at all in windows, succeeded in Linux, then complain about it. I think your problem is with windows rather than linux.

Can you right click on the drive in windows and reformat it?

---

### Post by veraction on 2005-08-28
> Let me get this right. You couldn't do this job at all in windows, succeeded in Linux, then complain about it. I think your problem is with windows rather than linux.

Can you right click on the drive in windows and reformat it? 

I want to be able to use the drive in both windows and linux and be able to write to it in linux (therefore no NTFS). Windows XP will not format a large drive/partition with FAT32. The only option is NTFS.

Gparted seemed like it would format the partition as FAT32, but when I switched over to windows, I realized it isn't true fat32 since it wasn't recognized

----

"succeeded in Linux" These linux programs did not succeed.

I'd much rather use linux. But I know if I have any little problem, it'll take 12+ hours to troubleshoot it while I never would've had the problem in the first place with windows

---

### Post by manicka on 2005-08-29
[QUOTE=veraction]nt[/QUOTE]
 very clever  [-X

good thing you can't delete the quotes in our posts as well

---

### Post by veraction on 2005-08-29
Yes, good thing I can't.

I was able to successfully format the drive when I got my hands on a copy of Partition Magic. Many attempts at doing so in linux via fdisk/cfdisk, gparter, mkfs failed.

I plan on using Linux 99% of time. Only exception is if I need dreamweaver for fixing up some documents.

Don't see why you started a flaming in the middle of a tech post

---

### Post by manicka on 2005-08-29
[QUOTE=veraction]Don't see why you started a flaming in the middle of a tech post[/QUOTE]

Not a flaming. 
I don't understand why you would ask for help for problem caused by windows, then get annoyed with Linux when you can't fix it.

> No wonder why so little people use linux :( 

I also don't understand why you would delete the content of your posts when you get a reasonable criticism of that comment. Especially considering that this was followed by further help/idea to solve your problem.

I'm glad things worked out for you :)

---

### Post by ubuntme on 2005-08-30
fdisk and mkfs would have done it just fine, however windows being windows, makes it difficult.  When you format using mkfs (or is it when using fdisk to partition?? I can't remember) there is an option so that you can label the partition as a windows partition.  This is not a default option, but windows won't access the drive without this option selected.

The details would be in man fdisk or man mkfs

---

