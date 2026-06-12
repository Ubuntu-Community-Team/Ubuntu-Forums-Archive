---
title: "repair an ext3 partition"
date: 2009-04-02
forum: Desktop Environments
---

### Post by cybernet on 2009-04-02
how can i do that ?
i have a secondary hdd with windows and a ubuntu 8.04 live cd

if this helps

i searched on google
nothing is working

any help #-o ?

---

### Post by taurus on 2009-04-02
Describe the problems with your ext3 partition that you have first.  What is wrong with it?

---

### Post by sheshbesh on 2009-04-02
@OP
Could you provide more details on how it got broken? what used to be on it?
In any case, I would start with a back up. If it is really broken, this means you'll have to use dd to back up bit by bit.
After backup, you may want to try testdisk and photorec (both under the testdisk package).
Another possibility is to just create a partition with fdisk that starts and ends at the same sectors as the old one. If this partition used to be on the entire drive, this is easy (use fdisk's defaults). However, if you have other partitions on that drives, we can still check the number of sectors (with dumpe2fs) but this is more complicated, and before we help you with that, you should post the output of "sudo fdisk -l"

---

### Post by cybernet on 2009-04-02
> **sheshbesh said:**
> @OP
... you should post the output of "sudo fdisk -l"

sorry for this
( when i said "repair" what did you had in mind ?
if i could bootup my ubuntu i've known to run fsck on my hdd )

i had Ubuntu 8.04.2 Desktop on this hard
it's a sata2 - 250 GB
i have ( hopefully not "had" ) a www with 78200 files ( about 2 GB )
and about 80 databases with max. size of 6 GB

i have a backup on those
but i don't have a backup on my music ( 24 GB ) ( personalized music )
movies ( 80-120 GB )

and some personal data

if you guys understand something from this image please translate in english
( i receive this errors when i try to boot my Ubuntu :(( )

thank you


new discovery :D
i can access every file on my hard drive with linux reader from windows
but i can't boot
i'm revealed :D

---

### Post by pastalavista on 2009-04-02
You can boot from a live CD and run fsck on the drive with it...

---

### Post by cybernet on 2009-04-02
> **pastalavista said:**
> You can boot from a live CD and run fsck on the drive with it...

will resolve the boot problem :???:

---

### Post by sheshbesh on 2009-04-02
this should help you understand the dmesg lines that you posted:
[http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages)

i actually dont really understand the english of YOUR last message, could you please rephrase it?

you can always run "fdisk -l" "fsck" and even install the testdisk package when you run a live cd.

again, i recommend backing up everything before you start tinkering with it. just buy a 300GB external and from the live cd, open a terminal and run "dd if=/dev/sdx of=/dev/sdy" where sdx is the device name of your old (250GB) drive, and sdy is the device name of your new (300GB) drive. you can find the device names with "sudo fdisk -l" or with "sudo lshw". please note that every time you unplug/plug these drives, their device names change! so be very careful about the names before you run this command.

i really think you should post here the output of "fdisk -l"

---

### Post by pastalavista on 2009-04-02
> **cybernet said:**
> will resolve the boot problem :???:

it will if that is the reason it won't boot. do you even see a grub screen? if so, have you tried recovery mode?

---

### Post by cybernet on 2009-04-02
> **sheshbesh said:**
> just buy a 300GB external and from the live cd, open a terminal and run ....

do you think i can just go to the shop and buy the hdd
i need money for thatm about 80 euro
btw, i'm not rich

i will try with a live cd :D

---

### Post by sheshbesh on 2009-04-02
Buddy, a friendly advice: if the data is important for you, then you should back it up before you start recovering it. It may seem expensive now, but when you lose it, you'd wish you spent these $50 for a back up drive. Trust me, you don't want to be there... 
And I hate to say it for the third time, but if you really want some help, you should post here the output of "sudo fdisk -l". 
Have fun!

---

### Post by pastalavista on 2009-04-02
> **sheshbesh said:**
> Buddy, a friendly advice: if the data is important for you, then you should back it up before you start recovering it. It may seem expensive now, but when you lose it, you'd wish you spent these $50 for a back up drive. Trust me, you don't want to be there... 
And I hate to say it for the third time, but if you really want some help, you should post here the output of "sudo fdisk -l". 
Have fun!didn't want to insult the OP's intelligence by stating the obvious, but right you are.. backup.. always.. at least what you want to keep

---

### Post by andrea000 on 2009-04-03
you said you could access every file with a Linux reader from 
windows and this drive is a dual boot win/ubuntu .Does it boot 
directly into windows or does it give you the option to boot 
into ubntu?Did you reinstall windows or do anything like that 
and leave ubuntu alone if so your problem is not the partition 
its grub and that's a easy fix.I reinstalled windows when i was 
dual booting and left ubuntu alone but i run win xp in virtual 
box now i only run one windows program and that is for work.

---

### Post by cybernet on 2009-04-05
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d49e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00abcca6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         246     1974240+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 200, 19)

---

### Post by cybernet on 2009-04-05
root@ubuntu:/home/ubuntu# fsck -y -t ext3 /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 373 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

---

### Post by andrea000 on 2009-04-05
Were did you get the log file from if you can't boot into
ubuntu?Does grub come up when you turn your pc on and show 
a menu of the os?Can you provide more details on how it 
got broken it doesn't sound like it's the partition.

---

### Post by cybernet on 2009-04-05
> **andrea000 said:**
> Were did you get the log file from if you can't boot into
ubuntu?Does grub come up when you turn your pc on and show 
a menu of the os?Can you provide more details on how it 
got broken it doesn't sound like it's the partition.

i get this log from a live cd
situation changed i mean i format my hard drive then i tried to install windows but it gave me a hard drive error :mad:


now please tell me how can i repair my hard drive
i will post the error in 2 minutes

---

### Post by andrea000 on 2009-04-05
if you did a format from cd and you boot into windows and 
it doesn't even show ubuntu if that is so and ubuntu is still there it's 
grub or better yet you don't have grub download grub super disk .iso if 
burning from windows.download the file from the bottom of this page [here]("http://supergrub.forjamari.linex.org/?section=download") 
or the new auto super grub [here]("http://download.cnet.com/Auto-Super-Grub-Disk/3000-2094_4-10829335.html?part=dl-10829335&subj=dl&tag=button") burn to cd then boot into it.That's it the 
website should tell you anything you need to know but the disk is straight 
forward so you shouldn't have any problem.I have only used the first one but it
works great.


post back and tell me if it works

---

### Post by andrea000 on 2009-04-05
you may need to refresh the web page i just went there
and it loaded slow

	
boa sorte

---

