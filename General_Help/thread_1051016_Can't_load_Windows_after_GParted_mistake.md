---
title: "Can't load Windows after GParted mistake"
date: 2009-01-26
forum: General Help
---

### Post by ojhall11 on 2009-01-26
I was resizing my partitions in GParted on a live CD and I attempted to move my Windows partition 1 MiB to the left (for some reason it was 1 MiB from 0). When I saw this would take about 40 minutes I stupidly hit cancel and now I can no longer use GParted or boot Windows. When I try to boot into Windows it says there is an error and to press ctrl+alt+delete to restart. All I wanted was to resize my Windows partition and install Linux on its own partition. GParted now shows the Windows partition as if it actually completed the operation and has a warning symbol next to it that gives this when clicked:

[[img]http://img205.imageshack.us/img205/5663/19678442np6.th.png[/img]](http://img205.imageshack.us/my.php?image=19678442np6.png)

The problem is I don't have access to Windows so I can't do a chkdsk. It must be a simple problem of pointers or something cause GParted had only about 5 seconds to do anything. Also I'm relatively new to Linux and I've never extensively used a command prompt. Hopfully I can fix this so I can recover valuable files and get both Windows and Ubuntu back on my desktop.

I appreciate any and all help to fix my blunder.

---

### Post by BrandonBan6 on 2009-01-26
I don't think it is possible to arbitrarily resize a partition with Windows already installed on it. (though I could be wrong there). If you have your Windows setup disc you can boot to it, go into repair and try a repair install or boot to a command window from there and run chkdsk.

---

### Post by caljohnsmith on 2009-01-26
It looks like the first thing you should try would be to run a chkdsk on the partition, so if you have your Windows Install CD, how about booting that, go to the "recovery console" and do:
```
chkdsk /r
```
If you don't have a Windows Install CD, you can instead download and use a Windows Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). Let me know how that goes.

---

### Post by ojhall11 on 2009-01-26
I tried all the recovery option from the upgrade cd I have and it looks like the partition isn't recognized as having anything to do with Windows. It, in fact, says it is a RAW drive. I may be trying to chkdsk the wrong location, but i assume that c: would be where it is. I'm going to try this other live CD option and i'll get back to you. I have labs till 4pm, however, so it will be after then. 

Thanks for the help.

---

### Post by caljohnsmith on 2009-01-26
It might possibly be that gparted recorded the new (erroneous) partition size for the Windows partition in your HDD's partition table without actually resizing Windows, so part of the problem might be that the ending sector for the Windows partition is invalid right now. That could affect whether chkdsk will run on it I think. How about checking if that is the problem by first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
Make sure you are using testdisk 6.9 or later, because earlier versions tend to crash when you try and list the directories of NTFS partitions. If you don't have 6.9 or later, let me know. After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each NTFS partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which NTFS partitions give you a directory listing. Also, please post the output of:
```
sudo sfdisk -l
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by Bigneil on 2009-01-26
i have used testdisk in ubuntu to fix my XP that i once minced up.  it worked very well. but... i ran a program called photorec first, and retrieved important data and backed it up before starting testdisk. you can run them both from your terminal

---

### Post by -kg- on 2009-01-26
> **ojhall11 said:**
> I tried all the recovery option from the upgrade cd I have and it looks like the partition isn't recognized as having anything to do with Windows. It, in fact, says it is a RAW drive. I may be trying to chkdsk the wrong location, but i assume that c: would be where it is. I'm going to try this other live CD option and i'll get back to you. I have labs till 4pm, however, so it will be after then. 

Thanks for the help.

I'm afraid that you have committed a (or possibly a couple of) partitioning "faux pas."  I have seen this before (when I did it myself - :oops: ).

First of all, never, *ever* interrupt a partitioning operation!  You will get the results you have experienced.

I was going to ask you if it was just this partition that showed as RAW, but I re-read your post and answered that question.  I seriously don't know if you will be able to recover your Windows partition or any data contained on it.  Someone else might be able to answer that question...I know I wasn't, and lord knows I tried!  I had to do a complete format and fresh re-install.

Second, if you see space to the left of your first Primary partition (i.e., all the way to the left of the graphical bar representation of the drive you're working on), DO NOT try to expand the partition into that space!  That is where the MBR (like GRUB or the Windows Bootloader) and the Partition Tables reside.  You may have overwritten the MBR and Partition Table for the drive, which would result in your not being able to boot to Windows.

Hopefully, someone will read this who has a bit more knowledge than me, but I think that you may have hosed your hard drive (as I did once, so don't feel bad).

<edit> To the later posters:  I sincerely hope you all can help this person, but when a Partition editor shows the partition as RAW, it means that the partitioning scheme is not recognized.  I do hope you're right and I'm wrong.

---

### Post by caljohnsmith on 2009-01-26
> **-kg- said:**
> 
Second, if you see space to the left of your first Primary partition (i.e., all the way to the left of the graphical bar representation of the drive you're working on), DO NOT try to expand the partition into that space!  That is where the MBR (like GRUB or the Windows Bootloader) and the Partition Tables reside.  You may have overwritten the MBR and Partition Table for the drive, which would result in your not being able to boot to Windows.

Gparted will never allow you to move the first, physical partition starting point so that it overwrites the MBR, so that's fortunately not a concern. But if ojhall11 moved the starting sector of the Windows partition at all, that usually breaks Windows so that you can't boot it after that without quite a bit of hacking. But moving the starting sector of the Windows partition will not itself make the Windows partition unmountable/unreadable, so that's actually a different issue most likely caused by aborting the partition change I think.

---

### Post by -kg- on 2009-01-26
> **caljohnsmith said:**
> Gparted will never allow you to move the first, physical partition starting point so that it overwrites the MBR, so that's fortunately not a concern. But if ojhall11 moved the starting sector of the Windows partition at all, that usually breaks Windows so that you can't boot it after that without quite a bit of hacking. But moving the starting sector of the Windows partition will not itself make the Windows partition unmountable/unreadable, so that's actually a different issue most likely caused by aborting the partition change I think.

OK, I didn't know that, but I wouldn't do that anyway, just in case.  Yes, I think it most likely the problem was caused by the aborted partitioning operation.  My problem was a bit different, but with the same results.  My partitioning editor would not recognize the partition as a partition formatted to any kind of recognizable format, and showed it as RAW, and in my case, with multiple partitions on the drive, it showed the *whole drive* as RAW.

As I found out (with Partition Doctor...my Windows installation was still bootable) I had somehow managed to "create" a Primary partition within the Extended partition.  How, I don't know...this happened using GPartEd, and GPartEd isn't supposed to allow *that* to happen, either.  That's why I take a chance with _nothing_ involving partitioning operations...GPartEd might be set up to not allow something to happen, but that doesn't mean that it *won't* happen.  In my case, it did!  :p

---

### Post by ojhall11 on 2009-01-26
> **caljohnsmith said:**
> It might possibly be that gparted recorded the new (erroneous) partition size for the Windows partition in your HDD's partition table without actually resizing Windows, so part of the problem might be that the ending sector for the Windows partition is invalid right now. That could affect whether chkdsk will run on it I think. How about checking if that is the problem by first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
Make sure you are using testdisk 6.9 or later, because earlier versions tend to crash when you try and list the directories of NTFS partitions. If you don't have 6.9 or later, let me know. After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each NTFS partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which NTFS partitions give you a directory listing. Also, please post the output of:
```
sudo sfdisk -l
sudo fdisk -lu
```
And we can work from there if you want.



Ok. I followed your instructions and I got a readout from testdisk:

[[IMG]http://img177.imageshack.us/img177/9875/td11yu5.th.png[/IMG]](http://img177.imageshack.us/my.php?image=td11yu5.png)

The first one didn't give me a directory listing:

[[IMG]http://img177.imageshack.us/img177/7992/td22gs8.th.png[/IMG]](http://img177.imageshack.us/my.php?image=td22gs8.png)

Here is the ouput you asked for:

> 
sudoubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  35872-  35873- 288148480    7  HPFS/NTFS
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bf313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   576297022   288148480    7  HPFS/NTFS


I hope this answers some questions. Thanks for all the help.

---

### Post by caljohnsmith on 2009-01-26
OK, that's not a good sign if testdisk can't read any of the NTFS partitions it found. How about running testdisk again, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, how about posting the output of:
```
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
```
And we can work from there.

---

### Post by ojhall11 on 2009-01-26
> **caljohnsmith said:**
> OK, that's not a good sign if testdisk can't read any of the NTFS partitions it found. How about running testdisk again, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, how about posting the output of:
```
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
```
And we can work from there.


Well it didn't read the first NTFS partition it found, but it did read the others. I don't know if that improves anything.

---

### Post by caljohnsmith on 2009-01-26
> **ojhall11 said:**
> Well it didn't read the first NTFS partition it found, but it did read the others. I don't know if that improves anything.
Did the second NTFS partition listed in your first screen shot give a directory listing? If so, before we go any further, I would recommend using your left/right arrow keys to navigate through that partition, select your personal files one by one, and press "c" to copy them to the directory where you ran testdisk. Once you have your personal files backed up, you could run the testdisk procedure from my previous post in order to try and recover the partition.

---

### Post by ojhall11 on 2009-01-26
> **caljohnsmith said:**
> Did the second NTFS partition listed in your first screen shot give a directory listing? If so, before we go any further, I would recommend using your left/right arrow keys to navigate through that partition, select your personal files one by one, and press "c" to copy them to the directory where you ran testdisk. Once you have your personal files backed up, you could run the testdisk procedure from my previous post in order to try and recover the partition.


yes it did! I'll do that now, thank you!

---

### Post by ojhall11 on 2009-01-27
> **caljohnsmith said:**
> OK, that's not a good sign if testdisk can't read any of the NTFS partitions it found. How about running testdisk again, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, how about posting the output of:
```
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
```
And we can work from there.

I backed up some files and followed your instructions. Here is what I got: 

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

---

### Post by caljohnsmith on 2009-01-27
So did you do the "Rebuild BS" procedure in testdisk? If so, how about booting your Windows Install CD, and again try:
```
chkdsk /r
```
If that doesn't work, then go through the same steps in post #11 again, except choose "Repair MFT" rather than "Rebuild BS". After that, try mounting the partition again, and please post the results.

---

