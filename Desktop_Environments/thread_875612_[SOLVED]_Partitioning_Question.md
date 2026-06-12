---
title: "[SOLVED] Partitioning Question"
date: 2008-07-31
forum: Desktop Environments
---

### Post by Unanimated on 2008-07-31
Okay, here's my (minor) issue.

I had Windoze on one drive on my computer (not a partition, it's own physical hard drive) and Ubuntu 8.04 on the other. I decided that I despise Windoze and love Ubuntu, but I still needed Windoze for my Nintendo Wifi Connector. I installed VirtualBox and got everything working beautifully, even the connector. So, deciding I didn't need a whole drive being taken up by an underused OS, I opened up Partition Manager from the live CD and formatted that drive under a Linux style. Now the drive won't show up in Ubuntu. What do I need to do to make it appear again? This is my second-to-last thing I need to complete before I'm completely finished setting Ubuntu up.

---

### Post by Tsarj on 2008-07-31
Does the partition show up in gparted?

---

### Post by rahmath on 2008-07-31
can u run the following command and post the output here;

$ sudo fdisk -l




this will show the partition tables on your system.

---

### Post by Unanimated on 2008-07-31
Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x190e190d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3579    28748286   83  Linux
/dev/sda2            3580        3738     1277167+   5  Extended
/dev/sda5            3580        3738     1277136   82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc070c070

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2497    20057121   82  Linux swap / Solaris

The 30.7 GB one is the one with Ubuntu on it.

---

### Post by rahmath on 2008-07-31
From that output, your second disk is completely treated as SWAP. which will not show up as a filesystem.

So please delete the swap on the second disk, and create a usable file system. Thats all...

---

### Post by Unanimated on 2008-07-31
Define "usable file system.." Like NTFS or FAT32?

---

### Post by rahmath on 2008-07-31
Sorry for the confusion caused.

Please let me know how you want to partition this second disk. Based on that i will tell u?

1. How many partition do u required in this second disk?
2. Whatz the size of each?
3. What is the File System required on those partitions?

---

### Post by Unanimated on 2008-07-31
> **rahmath said:**
> Sorry for the confusion caused.

Please let me know how you want to partition this second disk. Based on that i will tell u?

1. How many partition do u required in this second disk?
2. Whatz the size of each?
3. What is the File System required on those partitions?
Well, I basically just want this disk as a useless second disk that I can use for extra storage.

---

### Post by rahmath on 2008-07-31
So i guess, u need only one partition. And there is only Linux installed, i again assumes the File system you might required is ext3 (if you would have answered my Q's i could avoid this guessing).

RUN WITH CAUTION.

$ sudo fdisk /dev/sdb

then you will get an fdisk prompt.

from there type "t"

then it will ask the partition number to toggle, so type "1"

then it will ask the Hex code, so type "83"

then save the partition and quit by typing "w"


Then run from the bash prompt 
$ sudo partprobe /dev/sdb


then create an ext3 filesystem
$ sudo mkfs.ext3 /dev/sdb1

thats all....

now you can mount it to a location which you need to use.

example;
$ sudo mkdir /mnt/second-disk

$ sudo mount /dev/sdb1 /mnt/second-disk

Thats all...

NOTE: Sorry to define everything in CLI, bcoz i used to CLI and i dont know much in GUI.

---

### Post by Unanimated on 2008-07-31
> **rahmath said:**
> So i guess, u need only one partition. And there is only Linux installed, i again assumes the File system you might required is ext3 (if you would have answered my Q's i could avoid this guessing).

RUN WITH CAUTION.

$ sudo fdisk /dev/sdb

then you will get an fdisk prompt.

from there type "t"

then it will ask the partition number to toggle, so type "1"

then it will ask the Hex code, so type "83"

then save the partition and quit by typing "w"


Then run from the bash prompt 
$ sudo partprobe /dev/sdb


then create an ext3 filesystem
$ sudo mkfs.ext3 /dev/sdb1

thats all....

now you can mount it to a location which you need to use.

example;
$ sudo mkdir /mnt/second-disk

$ sudo mount /dev/sdb1 /mnt/second-disk

Thats all...

NOTE: Sorry to define everything in CLI, bcoz i used to CLI and i dont know much in GUI.
Nothing showed up. Basically nothing happened.

---

### Post by vanadium on 2008-07-31
These were pretty nice instructions to format that drive, though. It is quite unlikely that nothing happened except if your PC was powered of while you were executing the commands.

It is wiser to copy commands and output of such commands. Now, you hardly provide any information, so it is hard to have a clue of what went wrong and to provide further help.

---

### Post by Unanimated on 2008-07-31
Wait, nevermind--I didn't read the part where it said reboot. Now it's available. Thanks.

---

### Post by rahmath on 2008-08-01
Hope now you are able to access the additional disk.

---

### Post by Unanimated on 2008-08-09
I got everything working fine, but when I open "20.5 GB Media," a lost+found folder appears, and at the bottom, it says 17.5 GB available. That shouldn't be true.

---

### Post by rahmath on 2008-08-10
That is TRUE.

lost+found -->Every partition has a lost+found in its upper directory. Files that were saved during failures are here. or we can say, If any files are detached from the filesystem due to a disaster, fsck may try to reattach them there.

then regarding your size --> first of all in a 20GB hdd, u will not be able to use full 20GB. practically it will be near to somewhere around 18 GB. then once you had specified a file system, the filesystem metadata will take another few amount of space based on the type ans size of the filesystem. so finally you will end up in around 17 GB usable space.

Thats it.

If you find this answer useful, pls dont forget to say thanks by clicking "blue colored icon" in the bottom of this post.

---

### Post by Unanimated on 2008-08-10
Ohhh, thanks!

---

### Post by ryanchang on 2008-08-10
This is a loosely related question, but for some reason I can't start a new thread: Anyway, I just got a new HP laptop (dv6000 or something) and came with Vista Home Premium. I didn't want to mess around with partitioning so I just inserted the Hardy live CD and installed it inside of Windows. Here's my problem: I have a 200 GB hard drive, but only 9.0 gb is used for ubuntu. I'd like full, if not more, access to the rest of the hard drive. I've already used up 4.5 on music! Here's my fdisk output:

> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc151cc3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28884   232010698+   7  HPFS/NTFS
/dev/sda2           28885       30401    12185302+   7  HPFS/NTFS


Thanks!

---

### Post by Unanimated on 2008-08-10
Uhm.. I'm not completely sure about this since I haven't done that for a while, but isn't there a dialog box in the installation that lets you choose the size of the OS?

---

### Post by ryanchang on 2008-08-10
At the time I was under the impression that it meant how much extra room I wanted to give the installation, not how much the partition would be. I think it only went up to 30 too. Is there way I could mount the section of the HD where Vista is installed?

---

### Post by Unanimated on 2008-08-10
If you go into the file browser, the folder that shows the drive that Ubuntu is installed on is called host. Double-click the folder, and all the files on the hard drive will appear.

---

### Post by ryanchang on 2008-08-11
Agh! I'm retarded. Guess I should've just spent a little bit more time looking; haha. Thanks so much!!

---

### Post by Unanimated on 2008-08-11
Glad I could help.

---

### Post by zuner2012 on 2008-08-12
try booting from a live cd. find the right hdd. format it in whatever will work for you. ext3, ext2, fat, fat 16 etc. etc.

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

