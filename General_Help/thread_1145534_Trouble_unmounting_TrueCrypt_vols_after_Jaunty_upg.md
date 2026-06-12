---
title: "Trouble unmounting TrueCrypt vols after Jaunty upgrade (device-mapper errors)"
date: 2009-05-01
forum: General Help
---

### Post by Pyriel on 2009-05-01
I hope someone can help me.  Since upgrading to 9.04 last week I've had problems unmounting my encrypted volumes with TrueCrypt.  Everything worked perfectly in 8.10.  After the upgrade I can mount the volumes just fine, but when I try to unmount them I get this error message:
> device-mapper: remove ioctl failed: Device or resource busy
After I click ok on that box, TrueCrypt still shows the volume as mounted.  However, the OS does not show the volume's file system as being mounted any more.  I browse out to the mount point and verify that it is no longer mounted.  If I go back to TrueCrypt and click on Dismount again, it clears out of the list with no errors.

A dmesg | tail reveals this error:
> [  225.477074] device-mapper: ioctl: unable to remove open device truecrypt1

So I browse out to /dev/mapper/ and watch it as I run through the process again.  When I mount the volume it does properly create a truecrypt1 device.  When I unmount and get the resource busy error, the file system unmounts from the OS but the device remains in mapper (and still shows as mounted in TrueCrypt).  When I click the Dismount button again the device is properly removed from mapper and cleared from the TrueCrypt interface.

I've searched around but haven't been able to find any solution yet.  Any help is greatly appreciated.

Thanks

---

### Post by lensman3 on 2009-05-01
This sounds like a problem with kernel revs.  Did you recompile from source the truecrypt code?  I have notice after a few kernel upgrades that the truecrypt executable get out of sync with the new kernel headers and needs to be re-built.  That has cleaned the problems I have had.

---

### Post by Pyriel on 2009-05-02
No, I downloaded the Ubuntu x64 .deb package off the TrueCrypt website.  I tried reinstalling the package when I noticed this problem, but it didn't help.

---

### Post by Pyriel on 2009-05-02
Thank you, I think I got it.  After hearing how your TrueCrypt got out of sync with the kernel headers I decided to try to reinstall again, but did it a little differently.  This time I did a complete removal via Synaptic first (I didn't do that last time, I just chose to reinstall the package in place.)  Then I installed the package again, and so far it seems to be working.  I think you're right, it just got out of sync with the new kernel and needed to be completely removed and installed fresh.  Reinstalling the package in place simply wasn't enough to refresh it.

Thanks

---

### Post by Pyriel on 2009-05-02
Scratch that last post - it is still an issue.  After the complete removal and re-installation I was able to do it a few times without the error.  I thought it was fixed.  That was short-lived, as today I am getting the error again.  It seems to be an intermittent issue - sometimes it does unmount properly, but more often than not it doesn't.

Any suggestions?

---

### Post by nehumanuscrede on 2009-05-04
Confirming the same problem as you are seeing.  

Brand new installation of 9.04 ( wiped the drive and installed direct from disc ) as well
as new installation of Truecrypt 6.1a  ( 9.04 32-bit desktop edition ) 

Truecrypt volumes mount with little issue.  Device mapper ioctl error upon trying to unmount the drive.  
Second attempt to unmount is successful and error free.   

No issues under 8.10     

Only started upon the upgrade to 9.04

Additional information:

Device appears to be dismounting even though the error displays.  

Beats the hell out of me. . . . .

---

### Post by Pyriel on 2009-05-05
I always assumed my problem was caused by some screw up during the distribution upgrade, so it's interesting to hear you have the same issue off a fresh install.

---

### Post by Pyriel on 2009-05-17
TrueCrypt 6.2 was released last week.  I installed it on my system a few days ago and have not seen the error since.  It looks like the update fixed whatever issue 6.1a had with Ubuntu 9.04.  Anyone who is having this issue should grab the newest version off the TrueCrypt site.

---

### Post by nehumanuscrede on 2009-05-28
6.2a is still exhibiting the same issues as 6.1 had shown. 

However, I'm beginning to wonder if the problem isn't related to the drive spinning
down ( E-Sata drive ) and being initially unavailable to Truecrypt when the dismount
command is sent.  

Will have to play with it some more.

---

### Post by user789 on 2009-09-30
I'm also having the same issue.

I installed Jaunty on a fresh build of hardware and it works great.
Installed version 6.2a of truecrypt.
I can mount a drive (without filesystem)
But I cannot dismount the drive via truecrypt.

Could this be caused by mounting without a filesystem then using gparted to format the truecrypt volume with NTFS?

Sorry if the question is ignorant but I'm very new to truecrypt and fairly new to linux.

Thank you in advance for any help.

---

