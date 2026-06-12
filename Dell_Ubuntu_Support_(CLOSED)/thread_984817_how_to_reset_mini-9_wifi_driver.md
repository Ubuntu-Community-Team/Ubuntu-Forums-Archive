---
title: "how to reset mini-9 wifi driver?"
date: 2008-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mageus on 2008-11-17
Anyone know how to reconfigure the wireless driver?


Mini 9, fresh install of Hardy, everything (including wifi) worked fine initially.  Was adding software, I lost wifi on a reboot.

I think that somewhere along the way the kernel was updated from 2.6.24-19 to 2.6.24-21.  However, since I didn't set up grub from this partition, my menu.lst wasn't updated, so I must have been running 2.6.24-19 when I did another apt-get upgrade.

Now the wifi chipset isn't even recognized when I boot into 2.6.24-21, but it works fine under 2.6.24-19.

Anyone know how to reconfigure the wireless driver?

---

### Post by starcannon on 2008-11-17
Heres a walk through, though it seemed like I did one of these on a dell a few months back and literally point and click installed it using the Hardware Drivers utility:
System>Administration>Hardware Drivers

Anyway, if that does not work then try:
[http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html](http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html)

GL

---

### Post by mageus on 2008-11-17
starcannon, thanks for the advice, but my situation is odd.

Upon install of 8.04.1 wireless was not available, but became enabled after the first apt-get upgrade.  Hardware Drivers never showed any driver available under 8.04.1.  Even tried installing linux-restricted-modules.

If I understand correctly, there are about 3 drivers out there, the Broadcom binary (that requires using b43-fwcutter), a 'wl' driver, and using ndiswrapper.

Which one is the driver that is installed automatically by apt-get?  I want to use something that will be updated by the repository.  ndiswrapper & the extracted binary don't fit that bill, and I have no idea what this 'wl' driver is.


Any ideas?

---

### Post by starcannon on 2008-11-18
> **mageus said:**
> starcannon, thanks for the advice, but my situation is odd.

Upon install of 8.04.1 wireless was not available, but became enabled after the first apt-get upgrade.  Hardware Drivers never showed any driver available under 8.04.1.  Even tried installing linux-restricted-modules.

If I understand correctly, there are about 3 drivers out there, the Broadcom binary (that requires using b43-fwcutter), a 'wl' driver, and using ndiswrapper.

Which one is the driver that is installed automatically by apt-get?  I want to use something that will be updated by the repository.  ndiswrapper & the extracted binary don't fit that bill, and I have no idea what this 'wl' driver is.


Any ideas?

On my default install the wl driver appears to be in use. Be sure to see this post as well, it will allow you to put a default dell ubuntu install on your mini9 using a usb thumdrive: [http://ubuntuforums.org/showpost.php?p=6201306&postcount=4](http://ubuntuforums.org/showpost.php?p=6201306&postcount=4)
Be sure to seed the .img when your done, dell pulled the link off their support site, and will likely pull it off the ftp server eventually as well, and its such a nice resource that it would be a shame for the community to lose it.

---

### Post by mageus on 2008-11-19
Thanx for the comments.

I went away from the Dell install because I wanted to use VirtualBox, which doesn't work on the lpia kernel.

I ended up reinstalling 8.04.1 and everything is working fine now.

In hindsight, I think it was a problem with the keyring manager, since I had a similar problem enabling wifi on the new install until the keyring manager finally asked for a default password.

---

### Post by starcannon on 2008-11-20
Out of curiousity, did you put an SDHC MMC in the media slot, or did you by a bigger after market SSD and drop it into the SSD bay? Mines only got 16gb, by the time I did an Virtual Box XP install, there wouldn't be much left for /home.

---

### Post by mageus on 2008-11-20
I have the 16Gb SSD and an 8Gb SDHC.

I partitioned the SSD:
- 8Gb - ext3, main boot
- 4Gb - ext3, currently using as a second install
- 4Gb - fat32, originally for WXP, but currently using for VirtualBox image
- I don't use a swap.

I only need VirtualBox for my work's VPN and for my car's diagnostic software, neither of which will run on Mac/linux.  A 3Gb XP install works fine for this.

I started w/ 8.10 on the first drive, but that ended up having problems with restart/suspend (something's wrong with the gnome Power Manager).
Then I installed 8.04.1 on the second partition, and I ran into problems with the wifi.

Now I've got a new 8.04.1 install on the 2nd partition, and I reformatted the 3rd partition to ext3 to copy over the 8.04.1 install for backup.

Now, I'm running into a kernel panic on resuming from standby on the 8.04.1 install.


Wish Dell would update its lpia repos.

---

