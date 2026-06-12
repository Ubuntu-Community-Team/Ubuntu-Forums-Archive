---
title: "Hard Disk Full but I still have 80 GB free - FSTAB problem"
date: 2005-12-12
forum: Desktop Environments
---

### Post by altuzar on 2005-12-12
Hi. I have a problem with my Fstab file, probably. I use 1 HD of 120 GB. There is a partition of 20GB for root (/) and Kubuntu system. And there is another of 100GB for downloads, music, videos, etc. It's mounted in /lucas. However, I don't have access for that partition and the Konqueror say my space is over. Buy I have only used 20 GB!!!

Here is my Fstab file in /etc:

proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /lucas          ext3    rw,user,auto,uid=1000,gid=1000,umask=0        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0

There you can't see but let me tell you that / is the 20GB partition (hda1) and /lucas is the 100GB partition (hda3). 

How can I get access to my 100GB partition?
Help PLZ xD

---

### Post by Zaventh on 2005-12-12
paste the output of "df"

---

### Post by GoldBuggie on 2005-12-12
Thing that you can try:

**[SIZE=3]Check that the /lucas directory exists[/SIZE]**
```
ls -d /l*
``` 
If it does not exists then create it
```
sudo mkdir /lucas
``` 
[SIZE=3]**Change umask so that it says 000.**[/SIZE]
```
/dev/hda3       /lucas          ext3    rw,user,auto,uid=1000,gid=1000,umask=000  0       2
``` 
To have the changes in effect without reboot do a
```
sudo mount -a
```.This remounts everything in fstab.

If you have looked into this already then sorry for posting it. Otherwise please try the *sudo mount /lucas* command and maybe you will get an error which you can report back or investigate.

---

### Post by altuzar on 2005-12-12
Zaventh: here is the result for "df":

S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/hda1             17085684  15379544    838232  95% /
tmpfs                   258244         0    258244   0% /dev/shm
tmpfs                   258244     12588    245656   5% /lib/modules/2.6.12-10-386/volatile

GoldBuggie: I did everything you said. /lucas directory already exist. When I type "sudo mount -a" here is the error answer:

mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

With "sudo mount /lucas" I get exactly the same error.

What can I do?????

---

### Post by psusi on 2005-12-12
Are you sure the partition was formatted for ext3?  If so, then it looks like it may have been corrupted.  After you get the failed mount, run dmesg and see if it has any related error messages.  

[QUOTE=altuzar]Zaventh: here is the result for "df":

S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/hda1             17085684  15379544    838232  95% /
tmpfs                   258244         0    258244   0% /dev/shm
tmpfs                   258244     12588    245656   5% /lib/modules/2.6.12-10-386/volatile

GoldBuggie: I did everything you said. /lucas directory already exist. When I type "sudo mount -a" here is the error answer:

mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

With "sudo mount /lucas" I get exactly the same error.

What can I do?????[/QUOTE]

---

### Post by altuzar on 2005-12-12
I have "dmesg". It says:

> [4403880.974000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4403881.096000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i
sa0060/serio0).

There's also the other error:
> [4429772.811000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

And that's it. I don't understand anything, sorry. I can imagine it's a fstab file error with the "uid=1000" option. I remember the kubuntu installer formated my disk. It was 20GB for /, 100GB for my binaries files for /lucas. I think both were Ext3 but maybe I'm wrong. I don't want to lose my data! The home directory is: /home/fer, but my music and videos are in /lucas.
Sorry for the problem. I didn't use Partition Magic. xD

---

### Post by psusi on 2005-12-13
The first error is just the kernel complaining about an unrecognized key on your keyboard.  The second is because the uid, gid, and umask options are not valid for the ext3 filesystem.  Those options are only used with vfat and ntfs, because windows does not store that information so you have to tell the kernel to fake it.  You should remove those options from that line in your fstab.  

By the way, can you READ any of the data on that partition?  

Try unmounting and remounting it and then looking at the last few lines that dmesg spits out.

---

### Post by altuzar on 2005-12-13
> 
By the way, can you READ any of the data on that partition? 

Yes, I can read the files and I can write them also. But the computer says that I only have a space for hd of 20 GB, when the actual and fisical drive is  a 120 GB HD. 
On the first and boot partition (/ or hda1) I should have only 2 or 3 GB for the system files of 5.1 Kubuntu and some other files and apps. 

I will make any sugestion. PZL :confused:

---

### Post by psusi on 2005-12-13
No no, I said can you read THAT partition ( the 100 gig one ), not your root ( / ) partition.  From the looks of it your problem is that you can not mount the partition at all.  I just wanted to make sure because that is not the same as the disk being full.  

I have two guesses as to what is wrong:

1) The partition is NOT formatted as ext3.  You originally formatted it as vfat or ntfs, which is why you had the uid and umask options set, but for some reason, changed the filesystem type in fstab to ext3.  

2) The partition has become corrupted.  

Try these two commands and see what happens:

sudo fsck.vfat /dev/hda3

sudo ntfsinfo -d /dev/hda3

If one of those comes back without all kinds of errors, then my first guess is correct and you should change the filesystem type back to the correct one in your fstab.  

[QUOTE=altuzar]Yes, I can read the files and I can write them also. But the computer says that I only have a space for hd of 20 GB, when the actual and fisical drive is  a 120 GB HD. 
On the first and boot partition (/ or hda1) I should have only 2 or 3 GB for the system files of 5.1 Kubuntu and some other files and apps. 

I will make any sugestion. PZL :confused:[/QUOTE]

---

### Post by altuzar on 2005-12-14
I can read and write the partition. 
When I type in terminal: 

> sudo fsck.vfat /dev/hda3
here is the answer:

> dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 155.

And when I type: 
> sudo ntfsinfo -d /dev/hda3
The compu says:
> 
sudo ntfsinfo -d /dev/hda3

Pleaze help me, I'm histerical HELP PLZ

---

### Post by altuzar on 2005-12-15
Problem solved now via IRC. Only a simple mounting operation. 
The line was:
> 
/dev/hda3  /lucas ext3 defaults  1   2

I had to move all the files there. The system was saving the files in /lucas but unmounted the partition of the hd. 

Thanks for the help!

---

