---
title: "Can't detect external hard drive"
date: 2009-06-07
forum: General Help
---

### Post by ubfu on 2009-06-07
running ubuntu live disc 9.04

at terminal 

ubuntu@ubuntu:~$ sudo lsusb 
Bus 001 Device 002: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

It does found "Sunplus Technology Co., Ltd" I don't know what is it actually , maybe the external casing brand but it's different brand.Having 500GB WD hard disk inside the external casing.

But ,It can't detect it at Computer or running partition editor (gparted)

Thank you , hope someone can help me out.

---

### Post by ubfu on 2009-06-07
It detect at window , just tried 5 min ago and it detects my external hard disk but not in ubuntu 9.04

An attachment picture at 7th post
[http://ubuntuforums.org/showthread.php?t=1180904](http://ubuntuforums.org/showthread.php?t=1180904) 

Thank you

---

### Post by LewRockwell on 2009-06-07
why new thread?

---

### Post by ubfu on 2009-06-08
> **LewRockwell said:**
> why new thread?

Before , I plan to merge partition but now running ubuntu live , I am having problem detecting external hard drive.

Shouldn't be a new thread ? 

The external hard drive can be detect at window but not ubuntu.Anyone know why ?

---

### Post by ubfu on 2009-06-08
I am able to detect my external hard drive using old version of ubuntu 8.04 while the new version 9.04 can't.

Anyone knows why ? help ?

---

### Post by kpkeerthi on 2009-06-09
Connect your external HDD, wait for a few seconds and then post the output of the below command:
```
sudo fdisk -l
```

---

### Post by ubfu on 2009-06-09
Did that , it doesn't work.

---

### Post by sendblink23 on 2009-06-09
Can you explain the plan that you have with your External Hard Drive?

Since I read before you mentioned on Live CD of 8.04 the External HD was recognized... so why don't you use it there instead?

---

### Post by ubfu on 2009-06-09
> **sendblink23 said:**
> Can you explain the plan that you have with your External Hard Drive?

Since I read before you mentioned on Live CD of 8.04 the External HD was recognized... so why don't you use it there instead?

I haven't install any of those version.I am still thinking whether I should choose 8.04 or 9.04 Jaunty Jackalope.
If there's a workaround to fix this problem on Jaunty Jackalope , I'd surely go for Jaunty Jackalope.

I really hope someone can help me fixing this issue.
Isn't that weird where older version able to detect it while the newer version doesn't.
[http://ubuntuforums.org/showthread.php?t=1182482&page=2](http://ubuntuforums.org/showthread.php?t=1182482&page=2)

---

### Post by ubfu on 2009-06-10
Can I actually transfer the 8.04 usb detect configuration files and put it on 9.04 usb detect configuration ?

Sorry , newbie, is it possible ?

---

### Post by ubfu on 2009-06-16
And again , Is this problem normal for ubuntu ?

Does anyone know how to debug or fix it ?

I am still waiting for some help answer for over a week.:( Please

---

### Post by Derick01 on 2009-07-01
Hi,

Here is my suggestion for you.

The partition information is lost on the drive, so you can reset the
partition on Windows XP(etc) as such...

Connect the drive so it appears in your Device manager Goto My Computer, Right click, goto Manage Expand Storage and click Disk Management Your drive will be displayed  in the lower right portion of the screen It should be named somthing like DISK# and the data portion will be a black bar, and it should say "Unalloted" right click the bar and click create partition.

Make it a primary partition...
For all USB Drives, I suggest using FAT32.

---

### Post by ubfu on 2009-07-01
Sorry I don't understand , I am able to detect it on window XP and Ubuntu 8.04 Hardly but not in Jaunty 9.04.

There's no drive for me to mount but typing  sudo lsusb , it able to detect there's a drive connected to the USB port.
But , it still doesn't show the local disk.

Is it a bug on 9.04?

---

### Post by sideaway on 2009-07-19
Hmm, I appear to have this exact same isuue, I'm not sure if the OP fixed it, but I've got a toshiba MP3 player that I use as an external as well as a music player.

anyway, I get this:
```
sideaway@sideaway:/$ lsusb
Bus 001 Device 011: ID 0930:0009 Toshiba Corp. Gigabeat F/X (HDD audio player)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
after typing lsusb,
and then this after sudo fdisk -l
```
sideaway@sideaway:/$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa67ba67b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14217   114198021   83  Linux
/dev/sda2           14218       14593     3020220    5  Extended
/dev/sda5           14218       14593     3020188+  82  Linux swap / Solaris

```

any ideas?

---

### Post by paul@cyberengel.com on 2009-07-23
I've been having the same issue, (but I haven't tried 8.04 yet).  When I check dmesg I get the following:

Jul 23 13:01:44 paul-laptop kernel: [ 7415.824034] usb 2-2: USB disconnect, address 8
Jul 23 13:01:51 paul-laptop kernel: [ 7422.841093] usb 2-2: new high speed USB device using ehci_hcd and address 9
Jul 23 13:01:51 paul-laptop kernel: [ 7422.977247] usb 2-2: configuration #1 chosen from 1 choice
Jul 23 13:01:51 paul-laptop kernel: [ 7423.004200] scsi12 : SCSI emulation for USB Mass Storage devices
Jul 23 13:01:51 paul-laptop kernel: [ 7423.009209] usb-storage: device found at 9
Jul 23 13:01:51 paul-laptop kernel: [ 7423.009216] usb-storage: waiting for device to settle before scanning
Jul 23 13:01:56 paul-laptop kernel: [ 7428.009375] usb-storage: device scan complete
Jul 23 13:01:56 paul-laptop kernel: [ 7428.012833] scsi 12:0:0:0: Direct-Access     FUJITSU  MHZ2160BH G1          PQ: 0 ANSI: 2
Jul 23 13:01:56 paul-laptop kernel: [ 7428.013736] sd 12:0:0:0: Attached scsi generic sg2 type 0
Jul 23 13:01:56 paul-laptop kernel: [ 7428.100731] sd 12:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Jul 23 13:01:56 paul-laptop kernel: [ 7428.103014] sd 12:0:0:0: [sdb] Write Protect is off
Jul 23 13:01:56 paul-laptop kernel: [ 7428.103018] sd 12:0:0:0: [sdb] Mode Sense: 38 00 00 00
Jul 23 13:01:56 paul-laptop kernel: [ 7428.103021] sd 12:0:0:0: [sdb] Assuming drive cache: write through
Jul 23 13:01:56 paul-laptop kernel: [ 7428.106889] sd 12:0:0:0: [sdb] Assuming drive cache: write through
Jul 23 13:01:57 paul-laptop kernel: [ 7428.106893]  sdb:<6>sd 12:0:0:0: [sdb] Unhandled sense code
Jul 23 13:01:57 paul-laptop kernel: [ 7428.136911] sd 12:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 23 13:01:57 paul-laptop kernel: [ 7428.136916] sd 12:0:0:0: [sdb] Sense Key : Medium Error [current] 
Jul 23 13:01:57 paul-laptop kernel: [ 7428.136921] sd 12:0:0:0: [sdb] Add. Sense: Unrecovered read error
Jul 23 13:01:57 paul-laptop kernel: [ 7428.136926] end_request: I/O error, dev sdb, sector 0
Jul 23 13:01:57 paul-laptop kernel: [ 7428.136930] __ratelimit: 4 callbacks suppressed

---

### Post by ubfu on 2009-07-25
Hi , anyone knows the problem ? possible to fix it ?

---

### Post by ubfu on 2009-08-05
Any workaround ? Really need help thanks

---

### Post by Ramaddan on 2009-08-14
I have a similar problem to which this bug is related:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/23346]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/23346")

However, no fix yet, and I don't know if this problem continues in Ubuntu Karmic 9.10 or not.

I hope a fix is released at some point.

---

### Post by Magic_Spehar on 2009-08-26
Same problem here.  In Ubuntu 9.04 32-bit I could see my Western Digital External harddisk.  After changing to 9.04 64-bit I can't see my harddisk.
My harddisk does appear when I enter lsusb so it is detected...

The result of lsusb:

Bus 001 Device 006: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 011: ID 043d:011d Lexmark International, Inc. 
Bus 003 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by ubfu on 2009-10-27
So does this bug fix on ubuntu 9.10 ?

---

### Post by paul@cyberengel.com on 2009-10-27
Actually the issue was with the HDD... it had a password on it, so it only gets unlocked at boot.  (I haven't tested to see if USB works as well as SATA, just removed the pw.)

---

### Post by Lateralis on 2009-10-28
I upgraded from Jaunty to Karmic (9.04 -> 9.10) yesterday.  I've encountered a few problems, and this is one of them.  

Before, any USB flash drive and external hard drive I connected was automagically mounted.  Now, they don't mount at all.  I can see them when I go *lsusb* and *sudo fdisk -l*, but cannot/can't remember how to get them to mount in /media etc.  None of my drives have passwords on them and all used to work fine in previous versions of Ubuntu (7.10 up to 9.04).  This is most annoying as I use an external hard drive as my music storage unit as well as my research backup drive - all of my PhD and research work is backed up on this drive and without it, I am a little lost!  

I can get the drive to auto mount, but in order to do that I need to restart the laptop - less than helpful!  

As I said, this is something new to me as everything was fine in 9.04.  Don't quite know what's going on but is a definite bug with 9.10.

---

### Post by Lateralis on 2009-10-28
I pretty much take that back entirely.  

Whilst it may have automounted the first time I restarted, I have restarted twice since then and the OS has failed to mount it.  

I can manually mount it to a directory, but that is unsatisfactory as it was working perfectly fine before I upgraded to 9.10, and is added faff and hassle.  

Does anyone know what the Dickens is going on?

---

### Post by paul@cyberengel.com on 2009-10-28
My flash drives automount fine.  (I just double-checked before this post.)  Karmic even seems to handle the inserting/removing of my SATA drive tray without hiccup.

---

### Post by Lateralis on 2009-10-28
Seems rather bizarre. :/

All my drives used to mount just fine before I upgraded from Jaunty to Karmic.  But they don't now.  And I can't seem to figure out why.  I've tried tinkering with fstab, but I'm no expert.  Any advice would of course be appreciated.

---

