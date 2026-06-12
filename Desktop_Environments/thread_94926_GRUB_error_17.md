---
title: "GRUB error 17"
date: 2005-11-25
forum: Desktop Environments
---

### Post by syklitengutt on 2005-11-25
Hi.
I have Linux and windoes on to partitions,
and I got so pleased by Ubuntu that I wanted it to get more space.
I fired up windows, and started Acronis Disk Director Suite, and took some space
from sector D, hda5 and gave it to hda6 Linux.

When I booted up I got this errer.
GRUB loading error 17

and something about stage 1.5.

I coosed fixmbr and are now able to boot windows, but I need help to 
fiks the GRUB.

---

### Post by kosmic on 2005-11-25
Boot your Computer with a LiveCD and do a sudo fdisk -l and post the results where.
 
when you re-partition your hard drive, grub become confused because what was later (example - hda0,1 can become now hda0,2 because of the re-partition that you did)
 
The solution is to find the rigth root partition and install Grub again in the MBR pointing to the root filesystem so you can boot again ubuntu
 
 
sorry if it sounds a litle confused

---

### Post by syklitengutt on 2005-11-25
downloaded ubuntu-5.10-live-i386.iso
and booted it.
It goes trough all steps but when its about to start,
nothing happens.

Booting version 2.8 or something, and goes troug 4 steps I think and then
goes to a black screen with an __ in the top left corner.

---

### Post by syklitengutt on 2005-11-25
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3696    29688088+   7  HPFS/NTFS
/dev/hda2            3697       14593    87530152+   5  Extended
/dev/hda5            3697        6307    20972822+  83  Linux
/dev/hda6            6308        6361      433723+  82  Linux swap / Solaris
/dev/hda7            6362       14593    66123508+   7  HPFS/NTFS
ubuntu@ubuntu:~$

thats it...
Its changed....

---

### Post by syklitengutt on 2005-11-25
still need help.
The message over is what I got trough a live cd and sudo fdisk -l
what to do next.
Need a little bit of step by step explaining.

---

### Post by dyrer on 2005-11-25
Here is my fdisk -l
isk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11517    92510271    7  HPFS/NTFS
/dev/hda2           11518       24321   102848130    f  W95 Ext'd (LBA)
/dev/hda5           11518       24321   102848098+   b  W95 FAT32

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12847   103193496    7  HPFS/NTFS
/dev/sda2           12848       12978     1052257+  82  Linux swap / Solaris
/dev/sda3           12979       24321    91112647+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29652   238179658+  83  Linux
/dev/sdb2           29653       30401     6016342+   5  Extended
/dev/sdb5           29653       30401     6016311   82  Linux swap / Solaris

How can setup to work Windows, Ubuntu and SUSE 10

---

### Post by syklitengutt on 2005-11-26
Bump**
Still needs help with this.
I really dont want to format Ubuntu.

---

### Post by mrmcctt on 2005-11-26
First, I am not an expert.  But from this quote: > I coosed fixmbr and are now able to boot windows, but I need help to fiks the GRUB. it looks like you re-wrote your mbr with windows.

Check out [THIS LINK]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub") as it may explain how you can restore your GRUB.

Anyone feel free to correct me if I'm wrong.

---

### Post by magnusbb on 2005-11-26
The same happened to me when I resized my Ubuntu partition. It was a ReiserFS partition, and it simply became corrupted.

I have used ext3 since.

---

### Post by syklitengutt on 2005-11-26
didnt really got this to work.
Just boots up in windows after trying the first idea.
If I try the secound and type su in terminal I cant type the right passw.
dont know why...

---

### Post by kosmic on 2005-11-26
ok, easy way of puting GRUB in MBR again :
 
1&#186; Put the Install CD and Reboot the Computer
2&#186; Press enter when the boot CD show you a prompt
3&#186; follow the steps like you are doing a normal instalation
4&#186; when you get to the partition screen choose - Manual partition
5&#186; Give the same mount Points to the older partitions you have, (where you have to remember where you had / installed, /home installed etc)
 
*DO NOT CHOOSE TO REFORMAT*
 
after you are done simple click to save the modifications, and chosse next, after that the ubuntu linux will give you an error, just select continue.
 
In the next screen that apears, select INSTALL GRUB and install grub to your MBR, hd0, reboot and grub should start.
 
ATTENTION - if you gave to Grub the wrong mount points then when grub starts and if you click in any of the O.S. to start; Grub will split an error, in this case reboot the Computer, insert the Install CD and type 'Rescue' in the prompt, and chosse the Right mount points.

---

### Post by kosmic on 2005-11-26
[quote=syklitengutt]didnt really got this to work.
Just boots up in windows after trying the first idea.
If I try the secound and type su in terminal I cant type the right passw.
dont know why...[/quote]
 
because first you have to do sudo password
and after you gave root a new password you can do su in the terminal :)

---

### Post by syklitengutt on 2005-11-26
Ok... I got my GRUB up but it wont start UBUNTU.
This is how things look:

Ubuntu kernel 2.6.12-10-386
Ubuntu kernel 2.6.12-10-386 Recovery mode
Ubuntu kernel 2.6.12-9-386
Ubuntu kernel 2.6.12-9-386 Recovery mode

Other OS
Windows XP Pro

The error I get when selecting all of the Ubuntu selections is:
root (hd0,5)
Filesystem type unknown, partitipntype
0x82
Kernel /boot/vmlinuz-2.6.12-10-386
root=/dev/hda6 ro wuit splash
Error 17 cannot mount selected part


This I think is strange.
The OS should be on dev5 hd0,4
wtf is it trying to start 05 and hda6?

---

### Post by syklitengutt on 2005-11-26
it seems like grub is loading the wrong hda and hd.
How can I change this trough a live cd.--need step by step explanation.
They are now hda6 and (hd0,5) and should be hda5 and hd(0.4)
I cant use gedit as root trough the live cd. 
Get an error..

---

### Post by kosmic on 2005-11-26
ok with the live cd, mount your old linux / (root) partition
then use your favorite text editor (nano, vi, gedit etc) and open as root the following file :
 
sudo nano /boot/grub/menu.lst and change to te correct boot file :)

---

### Post by syklitengutt on 2005-11-26
ok... grub doesnt work and nano opens in terminal and I dont understand how to save the file trough nano....
and to mount its mount /media/dev5?
5 is my partition and hd0,4 is the other thing.

I really need a step by step explanation.

---

### Post by syklitengutt on 2005-11-27
bump

---

### Post by kosmic on 2005-11-27
[quote=syklitengutt]ok... grub doesnt work and nano opens in terminal and I dont understand how to save the file trough nano....
and to mount its mount /media/dev5?
5 is my partition and hd0,4 is the other thing.
 
I really need a step by step explanation.[/quote]
 
 
Ok first to save in nano just press [CTRL]+X it will ask you if you want to save the changes just press [Y].
 
to mount the drive
 
sudo mkdir /mnt/hda5
sudo mount /dev/hda5 /mnt/hda5
Then just follow the steps posted above

---

### Post by syklitengutt on 2005-11-27
ok...
Im in livecd now.
Ive checked hda1, hda5, hda7 and there is no 
menu.lst in any of these sektors!
It just creates a new file...
a blank one....
where to look now?

---

### Post by syklitengutt on 2005-11-27
here is my disk list:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3696    29688088+   7  HPFS/NTFS
/dev/hda2            3697       14593    87530152+   5  Extended
/dev/hda5            3697        6307    20972822+  83  Linux
/dev/hda6            6308        6361      433723+  82  Linux swap / Solaris
/dev/hda7            6362       14593    66123508+   7  HPFS/NTFS

content of hda5/boot/
root@ubuntu:/mnt/hda5# cd /boot
root@ubuntu:/boot# ls
System.map-2.6.12-9-386  config-2.6.12-9-386      memtest86+.bin
abi-2.6.12-9-386         initrd.img-2.6.12-9-386  vmlinuz-2.6.12-9-386

---

### Post by syklitengutt on 2005-11-27
ok... I created the grub/menu.lst in hda5/boot/
but that didtn change anything.
So any ideas of where the menu.lst that is used at startup is hiding on my
system?

---

### Post by syklitengutt on 2005-11-27
sorry about my nagging, but its been 3 days without linux now.
Anyone who can help me?

Where is my menu.lst
where is my grub
its hidden----

---

### Post by syklitengutt on 2005-11-27
Tnx for nothing really..
I managed it myselve...

Now to everyone if this happens to you.
In the selector screen where wou can choose what os to start,
simply select the bootitem that doesnt work,
press E and you can edit it from there....

Simple.... Why didnt anyone tell me this 3 days ago?

---

