---
title: "[SOLVED] How to: recover files from failed Wubi with LiveCD"
date: 2008-12-10
forum: General Help
---

### Post by Jammanuser on 2008-12-10
**How-To Recover Files from failed Wubi with LiveCD:**

Boot your computer, enter your BIOS by pressing the key it tells you to press at the first splash screen you come to at startup, put the CD/DVD drive first in the boot sequence, insert your LiveCD, then save the changes, and exit your BIOS.
Your computer should now boot from the CD.
In the Ubuntu setup program, select the preferred language you use, then select the "Try Ubuntu with No Change To My Computer" option.
Once at the Ubuntu desktop, in a Live session, open up Applications->Accessories>Terminal.

Run:
```

sudo fdisk -l
sudo mkdir /win
sudo mount /dev/sdxy /win
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

```
where the "x" and the "y" in "sdxy" is replaced with the correct HDD letter (starting at **a** of course), and the correct partition number (starting at 1), of the Windows partition your Wubi install is on. The first command will have given you the location.
Once running those commands, open up Places>Computer>Filesystem>vdisk, and you should find the contents of your root.disk in there. Now you can backup your data to external media, and reinstall Ubuntu with Wubi if you like.

You can also try running the 
```

sudo fsck /win/ubuntu/disks/root.disk

```
command to fix any filesystem errors that may be interfering with the boot, if that's the problem.

Hope it helps.

---

### Post by cardpogi on 2009-03-17
awseome gonna try this when i get home...:)

---

### Post by cardpogi on 2009-03-18
Not sure if anyone is gonna reed this... for some reason its gives me this error.. : (```
mount: can't Find /vdisk in /etc/fstab/etc/mtab
``` after i write this...```
sudo mount -o loop/win/ubuntu/disks/root.disk /vdisk
```

---

### Post by cardpogi on 2009-03-20
well i had a wubi installation and i bought a new laptop, i was passing all my windows folders, and some ubuntu but y killed my ubuntu boot.ini some time ago, so I uninstalled it and backed up my root.disk how can i boot from live disc to ubuntu and load the root.disk  to get some files? click [here]("http://ubuntuforums.org/showthread.php?t=1007816") to see where I'm up too...

---

### Post by cariboo on 2009-03-20
Have you created a mount point called vdisk?

Open an Applications-->Accessories-->Terminal and type:

```
sudo mkdir /vdisk
```

Jim

---

### Post by bapoumba on 2009-03-20
Threads merged.

---

### Post by cardpogi on 2009-03-20
> **cariboo907 said:**
> Have you created a mount point called vdisk?

Open an Applications-->Accessories-->Terminal and type:

```
sudo mkdir /vdisk
```

Jim

Yes I did
buts it's
```
/vdisk
```
not
```
/etc/mtab/vdisk
```

---

### Post by Jammanuser on 2009-03-21
You need to first run the commands
```
sudo mkdir /win
sudo mount /dev/sda3 /win
```
before the commands you mentioned, and replace the "sda3" with whatever partition it is that is your partition that contains the host OS (i.e. your Windows partition that contains your Wubi root.disk). The first command will create a virtual directory in the Live session called "win", and then running the second command will mount the host OS partition to that folder, and then you simply go on from there. ;)

The error you're getting indicates that you did not follow my exact instructions in the first post.

-Jam man

:guitar:

---

### Post by cardpogi on 2009-03-23
> You need to first run the commands
Code:

sudo mkdir /win
sudo mount /dev/sda3 /win

before the commands you mentioned, and replace the "sda3" with whatever partition it is that is your partition that contains the host OS (i.e. your Windows partition that contains your Wubi root.disk). The first command will create a virtual directory in the Live session called "win", and then running the second command will mount the host OS partition to that folder, and then you simply go on from there.

The error you're getting indicates that you did not follow my exact instructions in the first post.+

-Jam man



Yeah but I already did this... I followed all the steps...
But my problem is here...
> 
Code:

mount: can't Find /vdisk in /etc/fstab/etc/mtab

after i write this...
Code:

sudo mount -o loop/win/ubuntu/disks/root.disk /vdisk



Just mine is sda1 instead of sda3

---

### Post by Jammanuser on 2009-03-23
> **cardpogi said:**
> 
Just mine is sda1 instead of sda3

So did you enter in sda1 instead of sda3? 

EDIT: And I just realized I forgot to include the space between the "loop" and the "/win" in the command you just mentioned, so the command is actually

sudo mount -o **loop /win**/ubuntu/disks/root.disk /vdisk

and not

sudo mount -o **loop/win**/ubuntu/disks/root.disk /vdisk

My bad...first post fixed. Try it again, and it should work.

-Jam man

:guitar:

---

### Post by cardpogi on 2009-03-23
Ok Ill do this tonight, and tell you about it later on...

---

### Post by cardpogi on 2009-03-23
```
sudo mkdir /vdisk 
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

when I do this i get ```
mount: unknown filesystem type 'ext3'
```

any ideas?

---

### Post by Aravind_1729 on 2009-03-24
> **Jammanuser said:**
> For those of you who have had (or possibly will **have**) the "crc error" and then on next line "system halted" message, when trying to boot into a wubi install of ubuntu 8.10...and so can't boot into it, nor know how to recover your files from it into ur Windows (or other **main** OS)...here is a little something that i've typed up, to aid others with the same problem!

Well, here it is:

Ok...so here is the COMPLETE process of mounting your Windows partition, using a Ubuntu Desktop CD (or any other LiveCD!), and recovering your files:

```
sudo mkdir /win
sudo mount /dev/sda3 /win
```
Note: the “sda3” should be replaced (if not correct) with the correct partition that Windows is installed on! It was “sda3” in my case because the Vista partition (that contained my Wubi OS) was located in the third slot in the MBR partition table, therefore equaling the third partition, but the person should check first to see if it is the correct partition (by running "sudo fdisk -l" without the quotes in the Terminal). In my case, I had to automount the OS by going to Places>OS, and then opening up a terminal, ran “df” which showed me which partition the OS was on. If anyone wants to verify that I know what I’m talking about, here is the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won't%20boot"), in which can be found the same basic instructions, only in it they advise u to use “sda1” (which didn’t work for me, as Windows was on sda3). It also doesn’t describe how to recover your files…which is why I’m typing this right now! 

Ok…time to mount the virtual disk!!!

```
sudo mkdir /vdisk 
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

Now the content of the virtual disk can be viewed by simply opening up a file browser (Places>Computer>) and steering to the folder called “vdisk”, after first, of course, opening up the file system! Now simply (once inside of “vdisk”), go to “Home”, and there you will find all your important documents and files stored neatly inside of there (that is, of course, if when you had ubuntu working ok, you saved your work in your Home folder!).

You can also try running a filesystem check (even though it didn’t fix the problem, in my case…who knows! Maybe you’ll have better luck!):

```
sudo fsck /win/ubuntu/disks/root.disk
```

For me, all this did was recovered a “journal”, after which it said that the disk was “clean”…but when I tried booting into ubuntu, I still got the same crc error! But you should still try running it, just to wrap up all loose ends, and to make sure that you did all that you could to fix the error!

Oh, and one more thing! Before you can copy your files from your ubuntu disk into Windows, you will first have to run the following:

```
gksu nautilus
```
This command simply opens up the file browser as a root (administrator) user, so you can read and write the files that are therein! An alternative way to to copy files (using the Terminal) is:

```
cp
```
This is simply another method of copying!

Hope all this info helps somebody, and helps them to rescue their important files that are in their failed ubuntu! 

Cheers! :D

thank you very much, it helped my friend. now he is gonna stick to ubuntu!!!! once again thank you. it was simple and clear.

---

### Post by cardpogi on 2009-03-24
Relp!

---

### Post by Jammanuser on 2009-03-24
> **cardpogi said:**
> ```
sudo mkdir /vdisk 
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

**when I do this i get** ```
mount: unknown filesystem type 'ext3'
```

any ideas?

Ok...so this is a completely different problem you're having now. ;) The fact that its not recognizing the filesystem type of your Wubi install, even though it is ext3, means the root.disk itself may be corrupted. See, my tutorial is not intended for that scenario. It was mainly directed at other people who have a "crc error, system halted" message when trying to boot into their Wubi install, as I did, which I found to be not a problem with the actual virtual partition (i.e. the "root.disk" file stored on your Windows partition), but apparently a problem with the boot files that a Wubi install of Ubuntu 8.10 uses to boot, which FYI are not stored in the root.disk. In that scenario, the root.disk is perfectly ok, it is the boot files that are messed up, so the user can simply use this tutorial to rescue his files from the Wubi root.disk. But my tutorial is not intended for users who may have a corrupted root.disk to start off with, which AFAIK, usually requires a complete reinstall, and all loss of data stored within the root.disk unfortunately, unless someone else comes along who has a suggestion to fix this problem. :(

EDIT: Have you tried running the following command?
```
sudo fsck /win/ubuntu/disks/root.disk
```

Maybe it'll help...

---

### Post by Jammanuser on 2009-03-24
> **Aravind_1729 said:**
> thank you very much, it helped my friend. now he is gonna stick to ubuntu!!!! once again thank you. it was simple and clear.

Glad it worked ok for your friend, Aravind. :)
Let me know if he or you experience any problems, following the tutorial. FYI, I have learned quite a bit about the whole booting process since first writing this tutorial, as well as a couple of other things, so if you or him ever need any help with that either, I'll be glad to offer assistance. ;)

-Jam man

:guitar:

---

### Post by anur78 on 2009-04-29
Hi,
 
I am trying to mount the root.disk i.e Wubi Ubuntu fs on my  windows system. I dont have the root.disk in a separate partition. I have cygwin installed and when I do the following:
mkdir /umnt
mount C:\Wubi\Ubuntu\disks\root.disk /umnt
 
When I run mount on cygwin, I see the following, which means it has been mounted. 
C:\Wubi\Ubuntu\disks\root.disk on /umnt type system (binmode)
C:\Utils\Cygwin\bin on /usr/bin type system (textmode)
C:\Utils\Cygwin\lib on /usr/lib type system (textmode)
C:\Utils\Cygwin on / type system (textmode)
c: on /cygdrive/c type system (textmode,noumount)
u: on /cygdrive/u type system (textmode,noumount)
 
But, when I try to using cygwin browse for /umnt/home or any other folder using cd I dont see the folders. Can someone help me understand what I am missing here?
 
Thanks!

---

### Post by Jammanuser on 2009-11-12
> **anur78 said:**
> Hi,
 
I am trying to mount the root.disk i.e Wubi Ubuntu fs on my  windows system. I dont have the root.disk in a separate partition. I have cygwin installed and when I do the following:
mkdir /umnt
mount C:\Wubi\Ubuntu\disks\root.disk /umnt
 
When I run mount on cygwin, I see the following, which means it has been mounted. 
C:\Wubi\Ubuntu\disks\root.disk on /umnt type system (binmode)
C:\Utils\Cygwin\bin on /usr/bin type system (textmode)
C:\Utils\Cygwin\lib on /usr/lib type system (textmode)
C:\Utils\Cygwin on / type system (textmode)
c: on /cygdrive/c type system (textmode,noumount)
u: on /cygdrive/u type system (textmode,noumount)
 
But, when I try to using cygwin browse for /umnt/home or any other folder using cd I dont see the folders. Can someone help me understand what I am missing here?
 
Thanks!

Hello,

This is a tutorial on recovering your Wubi files with LiveCD, not with cygwin. I suggest you get help for your problem at the cygwin website. ;)

Cheers.

-Jam Man

:guitar:

---

### Post by efflandt on 2009-11-12
I have 9.10 bootable install iso on 4 G USB stick (made with USB Startup Disk Creator) which has 2.1 G file for persistent Linux data, leaving 1 G vfat free.  And it works for mounting the casper-rw file(system) from my desktop.

```
sudo mkdir /media/vdisk

sudo mount -o loop /media/HPUSB4G/casper-rw /media/vdisk

ls /media/vdisk
boot  cdrom  etc  home  lib  lost+found  media  rofs  root  tmp  usr  var
```

---

### Post by terryman007 on 2010-08-14
Get files from damaged system
go into recovery mode and root shell
***the command line***
first list disks


	```
sudo fdisk -l
```


then get disk mounted


	```
sudo mkdir /media/sdb1
```
where  sdb1 is the partition or disk that you want do mount


	```
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o
``` 

where vfat is you change to ntfs or ext2 or whatever the file system is(the fdisk command will tell you that)

then get to the folder

	```
cd /home/sammy/
```

then to copy entire folders or directories 

	```
cp -r foldersname /media/sdb1/
```

for example, I wanted to copy all my stuff in my home directory so I went to /home/ and 

	```
cp -r sammy /media/sdb1/
```
it took about fifteen minutes 

[COLOR="Navy"]***before***[/COLOR] you unplug your device.....

	```
sudo umount /media/sdb1
```

---

### Post by BLTicklemonster on 2011-03-13
Thank you, Jammanuser!!!

---

### Post by LORDNINIO on 2012-03-18
Sorry to drag up an old thread, but I've been using this method to retrieve my files after my Ubuntu 11.10 keeps hanging on start up. It gets to the Battery state check OK stage then just stops, this happened after a forced shut down when the laptop froze up. 

I have managed to retrieve most of my files, but it won't allow me to open folders such as mozilla, to get access to the bookmarks file. It just says I don't have access rights, or words to that affect.

Can anyone help me to get access to these files too?

Any help much appreciated, 

Cheers,

Andy

---

### Post by Jammanuser on 2012-03-19
> **LORDNINIO said:**
> Sorry to drag up an old thread, but I've been using this method to retrieve my files after my Ubuntu 11.10 keeps hanging on start up. It gets to the Battery state check OK stage then just stops, this happened after a forced shut down when the laptop froze up. 

I have managed to retrieve most of my files, but it won't allow me to open folders such as mozilla, to get access to the bookmarks file. It just says I don't have access rights, or words to that affect.

Can anyone help me to get access to these files too?

Any help much appreciated, 

Cheers,

Andy
Hi Andy.

Have you tried:

```

**sudo** cd PATH_TO_MOZILLA_FOLDER

```
?

-Jam Man

:guitar:

---

