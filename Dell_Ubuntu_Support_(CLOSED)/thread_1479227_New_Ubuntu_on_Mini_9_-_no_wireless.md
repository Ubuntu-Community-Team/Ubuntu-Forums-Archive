---
title: "New Ubuntu on Mini 9 - no wireless"
date: 2010-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by twentw on 2010-05-10
I just installed Ubuntu 10.04 on my Dell Mini 9.  It seems to be working OK, but I get no wireless connections.  If I pull down the the network menu, "Wireless Networks" is grayed out, and it says "disconnected".  I tried using "Connect to Hidden Wireless Network", but that didn't work either.  Any ideas?  Is there some sort of wireless card driver that I need?  If so, I can't find anything on Dell's site (even though many of these computers initially shipped with linux).

---

### Post by wojox on 2010-05-10
What type of card are you running:

```
lspci | grep -i net
```

Did you check Hardware Drivers?

---

### Post by twentw on 2010-05-10
Bear with me, since I'm not a linux person.  It appears I have a Broadcom BCM4312 802.11b/g.  I'm not sure where I'd find hardware drivers.  The only drivers Dell has on their website are for Windows.

---

### Post by gradinaruvasile on 2010-05-10
Ubuntu has the drivers bundled but not preinstalled for this wifi card.
My wife uses a Dell mini 9 with a 10.04 live stick since its HDD died - everything 
works out of the box - bluetooth, camera, microphone, wireless (it does need to activate the sta driver every boot, but no reboot required after that, just a 10 second waiting).

So,
Activate the STA driver (second in list) from "Hardware drivers" - this is located in the System->Administration menu. Wait 10 seconds (maybe less) and see if it is working. No restart required after the activation.

---

### Post by twentw on 2010-05-10
I tried that and it looked like it was going to work.  However, at the end, it failed saying "SystemError: InstallArchives() failed".  Any idea what the problem is?

BTW, I'm in the same boat as your wife - I'm booting off a flash drive because the SSD drive failed.

EDIT:  After a few reboots, it finally worked - although it never seemed to install properly.  Thanks for your help.

---

### Post by ugm6hr on 2010-05-11
In case others have a similar problem and come searching:
[http://ubuntuforums.org/showthread.php?t=1477215](http://ubuntuforums.org/showthread.php?t=1477215)

---

### Post by twentw on 2010-05-11
ugm6hr:  I'm trying to install get wifi to work on another flash drive installation, and it's not working.  When I do the "sudo dpkg" command, it gets to the point of "DKMS: install completed", and then says:

update-initramfs: deferring update (trigger activated)
lzma: Write error while encoding
dpkg: error processing bcmwl-kernel-source (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing bcmwl-kernel-source

Any idea what the problem is?

---

### Post by gradinaruvasile on 2010-05-11
I naver touched the terminal to install the wireless driver - the Hardware drivers activation script worked without problems every time.
Remember, i used the STA driver, not the first one on the list.

And i didnt use persistent install on the flash disk - i made 2 partitions, the first is with the .iso written on it, the second contains additional .debs (codecs for movies and mp3, skype, and a modified sources.list) and an installer script that installs everything.
Also, maybe it isnt helping here, but i removed the HDD (8 GB flash drive) as it wasnt working and filled dmesg with errors delaying boot.

---

### Post by ugm6hr on 2010-05-12
> **twentw said:**
> Any idea what the problem is?

Just carry on with the instructions.

The errors occur, since it cannot download from the web.  The later edits fix that.

---

### Post by JEBB on 2010-05-12
DM9, 16GB SSD, 2GB RAM
I upgraded to 10.04 from 9.04 via 9.10 and have no problem with WiFi.  

I do have problems with being unable to turn off the touchpad and waking it from sleep after closing the lid.

---

