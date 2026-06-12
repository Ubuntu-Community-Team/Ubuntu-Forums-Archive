---
title: "Restore MBR"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Master Shake on 2006-07-14
For purposes related to job-hunting, I had to install my Windows 2003 server trial CD.  Naturally, this replaced the MBR of my Dapper install.  How can I get the MBR / GRUB back?

For those who suggest anything using the Dapper CD, and trying to reinstall, it always hangs at the partitioner portion.

---

### Post by Sonofmoog on 2006-07-14
> **Master Shake said:**
> For purposes related to job-hunting, I had to install my Windows 2003 server trial CD.  Naturally, this replaced the MBR of my Dapper install.  How can I get the MBR / GRUB back?

For those who suggest anything using the Dapper CD, and trying to reinstall, it always hangs at the partitioner portion.

1) Go here and read the tutorial.  It is much too long to summarize here.

[http://www.chrysocome.net/dd](http://www.chrysocome.net/dd)

2) Download the file, and from Windows issue the command:

```
dd if=??? of=a:\Ubuntu bs=512 count=1
```

Substitute the path to your Ubuntu partition for the if=????  Also, this assumes a working floppy drive.  Substitute the path of your choice in the of= parameter, if you don't have a floppy drive.

3) Find the Ubuntu file you just created and move it to the root directory of Drive C:

4) Open boot.ini and add the following stanza as the last line

```
C:\Ubuntu="Ubuntu"
```

5) Save boot.ini and reboot.  If all went well, you'll see a Windows multi-boot menu with Windows and Ubuntu.  Select Ubuntu and press enter, and if things went really well, you'll see Grub.  Select Ubuntu again, press enter, and you should be on your way ..

HTH

A final caveat:  I have not used this program myself, though I have downloaded it, so I cannot attest that it works.

---

### Post by 5-HT on 2006-07-14
The previous post details how to configure Window's NTLoader to boot Ubuntu. 
If you want to get GRUB back on the MBR without using the install CD partitioner, the "Recovering GRUB automatically" and "Recovering GRUB manually" sections from following wiki page should help*: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

*NOTE: When installing GRUB to the MBR, make sure you specify the drive and not a partition!

HTH

---

### Post by Herman on 2006-07-14
> For purposes related to job-hunting, I had to install my Windows 2003 server trial CD. Naturally, this replaced the MBR of my Dapper install. How can I get the MBR / GRUB back?
For those who suggest anything using the Dapper CD, and trying to reinstall, it always hangs at the partitioner portion. The new 'Alternate' Install CD has a nice new graphical way to re-install GRUB. If you are the proud owner or an 'Alternate' Install CD, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")

If you have the 'Desktop' Live/Install CD, you can re-install GRUB to MBR from a GRUB shell in a terminal when the Live Operating system is running. If you want to see that, [*Click Here.*]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
(You do not need to run the installer to the partitioner stage at all to do that).

You can also do the same thing with the 'Desktop' Live/Install CD but rather than boot the Ubuntu Dapper LiveCD Operating system, boot the CD into 'Rescue mode' instead, and log in and type 'sudo grub' to get a grub shell and then install GRUB that way using the same method already given above (Grub Shell).

When you have GRUB re-installed, you can make a GRUB CD-RW to boot with in case that ever happens again, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD").

---

### Post by cotcot on 2006-07-14
You are not the only blocked with the partitioner of the liveCD.
The alternate CD works better. It is in textmode about the same as for breezy and allow using LVM and RAID.

---

