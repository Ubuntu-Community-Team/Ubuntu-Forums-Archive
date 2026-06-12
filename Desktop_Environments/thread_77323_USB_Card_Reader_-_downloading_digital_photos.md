---
title: "USB Card Reader - downloading digital photos"
date: 2005-10-16
forum: Desktop Environments
---

### Post by ColinG on 2005-10-16
Help please:( 

When I plug in my card reader I get the below error:

An error occurred while loading media:/sdb1:
The file or folder media:/sdb1 does not exist.

The media in the reader is Compact flash and it is read ok when I have it in my camera and use Digikam to download.

Thanks for your time
Colin

---

### Post by jeremy on 2005-10-17
This is a known problem, and there should be a fix for it soon. In the meantime, when this happens, you can navigate to your /media folder, and you will find your CF card there, probably under 'ubsdisk'.

---

### Post by ColinG on 2005-10-17
Thanks Jeremy
Colin

---

### Post by jeremy on 2005-10-18
It has been fixed now, you should do:
sudo apt-get update
sudo apt-get upgrade

More at [http://ubuntuforums.org/showthread.php?p=422977](http://ubuntuforums.org/showthread.php?p=422977)

---

### Post by ColinG on 2005-10-18
Many, many thanks Jeremy, but I've done a sudo apt-get update , sudo apt-get upgrade and whilst a couple of packages were upgraded the problem with USB is as before. Absolutely no change. Am I missing something? Regards Colin

Update:
Did first update on the 686 kernel and it was as above. Did it again on the 386 kernel and I got 43 updates. The usb issue has now gone away on the 386 kernel. Have yet to try 686. Maybe a timing thing?

---

### Post by ColinG on 2005-10-19
686 kernel is working. So what happened is this.

1) Whilst running on the 686 kernel I did an Adept update and upgrade. There were only two packages to upgrade and these had no impact on the usb problem.
2) Restarted Kubuntu using the 386 kernel, did an Adept update and upgrade and this time there were 43 packages to upgrade. This sorted the usb problem.
3) Rebooted back to the 686 kernel and all is well usb-wise.

So, the question is, why did Adept not pick up the updates when running on the 686 kernel (1 above)? Was it just a timing issue or is it something more sinister? Do I have to reboot into 386 mode to do all my updates/upgrades?

Many thanks
Colin:confused:

---

### Post by jeremy on 2005-10-19
I don't think that it should make any difference which kernel you are using (I am using 686 all the time), more likely a repo was temporarily unavailable or somesuch (but don't take that as authoratative!).

BTW, can you see you cd drive in media:/ now? Since the update I can't.

---

### Post by ColinG on 2005-10-19
The cd drive is not there by default but it shows up once I put a cd in the drive, Jeremy.

---

### Post by jeremy on 2005-10-20
I just checked, and you are right about CD's showing up when you put  a disk in the drive. But I can't see my 2nd SATA HD, sdb1, and can't find any setting that will show it. It is mounted, and I can view the contents in /media/sdb1.
It did show before the upgrade.

---

### Post by ColinG on 2005-10-20
I don't have a second linux drive. I do have an Windoze ntsf partition mounted though and that shows up in media.

---

