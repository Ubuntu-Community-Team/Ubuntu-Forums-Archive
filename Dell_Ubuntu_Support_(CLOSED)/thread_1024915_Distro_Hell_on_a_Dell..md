---
title: "Distro Hell on a Dell."
date: 2008-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TLimits on 2008-12-29
Having a new baby in the house and our catalog of digital pics expanding exponentially I decided it was was time to have an effective and simple data backup plan for our laptops and home office PC.

OK sounds simple. Dell Optiplex SX260 (2.53GHz no HDD) from Ebay ($50 inc shipping), I already had 1GB mem, 80 gig HDD and a Lan connection in the basement.

I have simple needs, a system that runs reliably (ok better add a UPS we get a lot of brownouts), can administer remotely (keeps me out of the basement!), an easy to use GUI, plenty of storage and syncs from the windows PC's automatically. 

Install Linux, add a USB 1TB drive, add some Samba shares and I should be good to go.... Wrong.... No problems with the hardware, however distro hell.

I wanted a mainstream OS (supportable) and LiveCD's are great as I can try before install. So I downloaded a few distros and tested on my HP Laptop all of them run great.

Now the problems.... I decided on Ubuntu 8.10 as its nicely supported and I love the look of it.

OK put the LiveCd in the Dell, booting up... nice splash screen... then nothing. Blank Screen.

I proceed to test the other CD's I had gathered and tested on my HP.

Fedora 10 - Login screen corrupt, can see dialog box but can not login.
OpenSuse 11 - Wierd flashing corrupt screen.
Kubuntu 8.10 - Same as Ubuntu, blank screen no GUI.
Xubuntu 8.10 - Same as other Ubuntu derivatives.
Puppy - Success it works... but not where I want to be.

OK I started reading and many problems with Dell SX/DX Optiplex's and the latest distro's.

Loaded Kubuntu 8.04 works fine on the LiveCd so I installed it.

Sweet! boots up fine, there's my Seagate 1TB usb drive. Setup shares no problem, windows PC's can see them.

One problem I can not get the Remote Desktop to work. It refuses to cooperate. Firewall is off I can ping the PC. Correct packages are installed. aaaargh. 

OK lets try Ubuntu 8.04...Hey everything loads, remote desktop works........ 1TB drive not mounted.... mount.... error can not mount. Hopefully this can be fixed. I'll apply all the package updates first and reboot to see if it will mount. On re-booting.... blank screen..... sames as 8.10.... this sucks.

Google says compiz maybe a problem... Reinstall (good job I have this on a bootable USB). Remove Compiz packages. Update all other packages reboot... Everything good still can not mount large USB drive. Google tells me to check that "usefree" is not an option in fstab. No "usefree" however I see that my drive dev/sdb1 is configured as a Cdrom..

/dev/sdb1 /media/cdrom0 udf,iso9660 ............ that does not sound correct. I created a new mount point and changed the line to 

/dev/sdb1 /media/backup ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

Rebooted and everything works..... A sync folder program is busily copying files from my PC's to the backup drive.

Can anyone tell me why the new distro's are so bad with the GUI issues on the Dell Optiplex?

Anyway Hardy Heron is great, my system does what I want it to. After this I will not be updating for a longtime.

Sorry for the long post.

---

### Post by adult swim on 2008-12-29
what type of video card is in the computer?

---

### Post by TLimits on 2008-12-29
Its the standard embedded video Intel 845G (I think).

---

### Post by adult swim on 2008-12-29
in the in 8.10 and above intel is using a new driver instead of the old one.  this is causing alot of problems with booting the system and nothing showing up but a black screen.  here is the bug report [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/285250](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/285250)

---

### Post by TLimits on 2008-12-30
Thanks.

I left a comment in the bug report thread, from my testing it appears to be Compiz that is causing the issue.

---

