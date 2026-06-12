---
title: "[media center] GRUB Error 17"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maraja on 2008-04-26
Hallo,

after one month of using my new Dell XPS 1330 I am now facing a big problem.
I decided to completely remove the preinstalled Vista using only Ubuntu with a couple of partitions.

Everything went fine until this morning when I was turning the notebook on; by mistake I pressed the Dell Media Center key (the one with the little house) and got a boot screen telling me something like: "please wait, the first time Media Center needs to create some files...".
I let it run until, as I expected, he told me that it was not possible to write on the hard disk (luckily I thought...).

Then I rebooted but cannot further the GRUB Loading screen where I am presented the "Error 17" and the system hangs.

Searched around and found the Super Grub Disk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) but it does not help.

I tried to boot with the live cd and, when I click the computer icon, I can see the following disks:
* cd
* 132gb (my second partition where I keep some data)
* MEDIADIRECT
* filesystem (the live cd itself)

it looks like my boot partition is not there anymore, is it possible that pressing the "Dell Media Center" key completely delete it?

Please help :(

---

### Post by ajmorris on 2008-04-26
hi there,
to fix this, we are going to re-install your grub into the Master Boot Record, so, do the following:

Boot into the live cd, then in a terminal:
```
1) sudo grub
2) find /boot/grub/stage1 (this will give an output of (hd#,#))
3) root (hd#,#)   (where #,# are the numbers found in step 2)
4) setup (hd0)
5) quit
6) reboot
```

Then, after your computer has rebooted, grub should load again :)

AJ

---

### Post by maraja on 2008-04-26
thank you AJ, unfortunately the "find /boot/grub/stage1" command reports:
**Error 15: File not found**

=(

---

### Post by ajmorris on 2008-04-26
> **maraja said:**
> thank you AJ, unfortunately the "find /boot/grub/stage1" command reports:
**Error 15: File not found**

=(

Perhaps you need to re-install grub. So mount your ubuntu partition on the live cd, (sudo fdisk -l can find what the /dev block device is called) Then just choot to where you mount the device, then in the chrooted environment, run sudo apt-get remove grub, then sudo apt-get install grub) then run teh commands again i said in my previous post.

---

### Post by MeanEYE on 2008-04-26
> **maraja said:**
> thank you AJ, unfortunately the "find /boot/grub/stage1" command reports:
**Error 15: File not found**

=(

The best way should be **fdisk** me thinks. It is possible only partition type was changed (but unlikely). As I recall some laptops do create small partitions 32MB in size for their own data. That might happened to you. Anyway when you check with **fdisk** and he does list some strange partition this small with unknown type this just might be it. My advice then to you is to just create patition from leftovers and install system again. There is no way to return data and by leaving this "Media Center" on you hard disk will prevent him from erasing your disk again.

---

### Post by ajmorris on 2008-04-26
> **MeanEYE said:**
> The best way should be **fdisk** me thinks. It is possible only partition type was changed (but unlikely). As I recall some laptops do create small partitions 32MB in size for their own data. That might happened to you. Anyway when you check with **fdisk** and he does list some strange partition this small with unknown type this just might be it. My advice then to you is to just create patition from leftovers and install system again. There is no way to return data and by leaving this "Media Center" on you hard disk will prevent him from erasing your disk again.

It is not necessary to re-install his system. Grub error 17 is that it cant find the grub files, because they are missing. Which means, either the partition was wiped, or the partition number was changed. By re-installing grub using the correct root partition (the one it was changed to from the media center install), grub wont get grub error 17 anymore.

---

### Post by maraja on 2008-04-26
here is the output of fdisk -l (manually copied from the broken system):

```
Disk /dev/sda: 200.0 gb, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x3000000

device    boot  start     end     blocks  id  system
/dev/sda1   *   23995   24322    2620416   c  w95 fat32 (lba)
/dev/sda2        6080    7052    7815622+  5  extended
/dev/sda3        7053   24321  138713242+ 83  linux
/dev/sda5        6080    7052    7815591  82  linux swap / solaris

partition table entries are not in disk order
```

I am not sure where the original Ubuntu installation could be, I guess there should be a device using blocks 1 to 6079 somewhere  but... where?
I guess the media center replaced the first entry (sda1) and, luckily, wrote its data at the end of the hard disk (if I remember well I left some unpartitioned space at the end of the disk).

Now how can I get back the proper entry for sda1?
Please provide detailed instructions about the commands to issue.

Another question is how is it possible that two entries (sda2 and sda5) share more or less the same blocks?

Before proceeding I hope to get some more clues as, if I have to reformat/reinstall, I will loose some vital data sitting on the main partition. 

If can get my data files back, you can bet in the future I am going to use only the second partition for that.

thank you for your support, 
impatiently waiting for more instructions,

---

### Post by maraja on 2008-04-26
RESOLVED!
:guitar:

I have found this message:
[http://ubuntuforums.org/archive/index.php/t-328392.html](http://ubuntuforums.org/archive/index.php/t-328392.html)

and fixed the problem using testdisk

Now it would be nice to know how to disable the "Media Center" in the BIOS, just to avoid the same problem in the future ;)

---

### Post by toorima on 2008-04-26
The easiest way to fix grub error 17 after pressing the media direct button is to press it again. Yeah it would be nice if it would be possible to have the key do something else.

---

### Post by Pin Millions on 2009-04-12
Well I went through the instructions for getting GRUB back, but when I went to load it, it came up with the old 8.04 kernals from before (I thought I'd) wiped the harddrive and installed 8.10 over it.

Then, when I loaded from the Live Disk again and mounted the harddrive, it came up with files and folders I'd had from my previous installation, again from before installed 8.10.

The laptop currently has no internet connection (Wifi isn't turning on; no ethernet around here), so can't install anything on it. Should I wait until I can install something, or just run the Live Disk over this mess and start again?

---

### Post by Pin Millions on 2009-04-12
Well, Wifi now works in the Live CD, which is guess is something. Ran fdisk, and got:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       30075       30402     2620416    c  W95 FAT32 (LBA)
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1322        9012    61777957+   7  HPFS/NTFS
/dev/sda4            9013       30402   171808424    f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   dd  Unknown
/dev/sda6   *        9013       29318   163107882   83  Linux
/dev/sda7           29319       30074     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order


Which seems kind of a mess, since the system had, up to yesterday, been behaving as if the hard drive was just one big 250GB Linux partition...

Any idea where that, and its files might be? Or why it's forgotten them and gone back to this?

---

### Post by meierfra. on 2009-04-12
Pin Millions: Lets see whether testdisk can find your old partitions:

booting into Ubuntu,  download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  /dev/sda

```

After starting testdisk with the above command, choose
"Proceed",
"Intel",
"Analyze",
"Quick search",
Press "Y" or "N" (depending whether you have any partition created by Vista)
Press "Enter" to continue,
select "Deeper Search" (so it does a deeper search, which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

### Post by Pin Millions on 2009-04-13
Thanks! I'd been trying to find Testdisk, but it's not in the repositories for new Ubuntus...

Here's what I got:
```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 29645 254 56  476262920
D FAT32 LBA               15   0  1  4192 254 63   67119570 [NO NAME]
D HPFS - NTFS             15  10 60  1320 117 13   20971520
D HPFS - NTFS           1321   0 11  9011 254 63  123555905
D Linux                 9012   2  1 29317 254 59  326215760
D Linux                 9027   1  1 29332 253 59  326215760
D Linux                 9028   2  1 29333 254 59  326215760
D Linux Swap           29318   1  1 30073 254 42   12145056
D Linux Swap           29646   1  1 30400 254 43   12128992
D FAT32 LBA            30074 239 54 30401  42 41    5240832 [MEDIADIRECT]
```

That's heartbreakingly wrong, surely?

I guess the reason the old Linux partition is still functionally in place is because, when I was dual-booting 8.04 and Vista, 8.04 was at the end of the disk and Vista the front, and when I installed Ubuntu Studio 8.10 in January (remembered my dates, now), it must have started at the beginning and still had more free space to go than the whole of the old partition (8.04 took up 187 GB, and I still had 180 GB free in 8.10).

So did Media Direct just write over the stuff at the front of the drive - the partition I want back? Why is it such a mess?

---

### Post by Pin Millions on 2009-04-13
>I should point out that I don't really mean "functionally in place" - all it's files are there when I mount it in the Live Disk, but it can't boot to it from the restored GRUB menu. it's gets as far as telling me it's look for files, after filling up a progress bar really slowly.

---

### Post by meierfra. on 2009-04-13
At the  screen after the deep search, use the up/down arrows to select the first Linux partition. Then use the left/right arrow to mark the  partition as "*".  Then select the second swap partition and mark it as "P".

The screen should now look like this

```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]* [/COLOR]Linux                    0   1  1 29645 254 56  476262920
D FAT32 LBA               15   0  1  4192 254 63   67119570 [NO NAME]
D HPFS - NTFS             15  10 60  1320 117 13   20971520
D HPFS - NTFS           1321   0 11  9011 254 63  123555905
D Linux                 9012   2  1 29317 254 59  326215760
D Linux                 9027   1  1 29332 253 59  326215760
D Linux                 9028   2  1 29333 254 59  326215760
D Linux Swap           29318   1  1 30073 254 42   12145056
[COLOR="Red"]P [/COLOR]Linux Swap           29646   1  1 30400 254 43   12128992
D FAT32 LBA            30074 239 54 30401  42 41    5240832 [MEDIADIRECT]
```

Press "Enter" to continue
Select the  "Write" tab and press "enter"
Press "Y" to confirm.
Then press "q" a few times to quit testdisk.

Reboot and hope for the best.

---

### Post by Pin Millions on 2009-04-13
I have levelled up to GRUB Error 22, which means that I at least have this year's partitions.

Shall I run the instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=224351"), which are what I did and got the old list of kernals last time?

Thanks for getting me this far!

---

### Post by meierfra. on 2009-04-13
> Shall I run the instructions from this thread,

Yes.  "find /boot/grub/stage1" should return "root (hd0,0)".

Then proceed with

```
root (hd0,0)
setup (hd0)
quit
```

---

### Post by Pin Millions on 2009-04-13
It's working!

Can I just ask: what does "swap" actually do? What did it mean when I marked the second one as P?

I ask because while booting up it only had a status bar for a short while, and one either side of that had a lot more text than usual (incl., for a nerve-wracking few seconds, just the legend "Looking for files to boot..." or whatever, where it used to snag), and in that text there was something about "Looking for swap", which got a red [fail] on the right hand side.

Did I make the wrong LINUX swap partition P? What would that mean? Is it related to showing lots of text instead of a loading bar on boot up, and now things being a bit slower than before?

---

### Post by meierfra. on 2009-04-13
>  what does "swap" actually do? 
Swap is used as virtual memory if your regular memory is used up.
But swap is also used during boot up to provide the Splash screen.

> What did it mean when I marked the second one as P?
This means that you want to use second swap partition as a primary partition.

```
Did I make the wrong LINUX swap partition P? 
```
I don't think so. The first swap partition overlaps with your Ubuntu partition. So  that cannot be the correct one.

But there does seem to be something wrong with your swap. Post the output of

```
cat /etc/fstab
sudo bklid -c /dev/zero
free
cat /etc/initramfs-tools/conf.d/resume

```

---

### Post by *drew on 2009-09-06
Thanks AJMorris. Your post on reinstalling Grub save me a lot of grief!

---

