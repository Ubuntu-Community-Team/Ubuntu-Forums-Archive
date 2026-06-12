---
title: "[SOLVED] Problem with upgrading bios on XPS M1530"
date: 2008-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Lacrimstein on 2008-06-11
Hi all, I want to upgrade my bios to A08 because it solves problems with the touchpad and makes wireless more stable.
I have followed the instructions on this page: [http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx]("http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx"). However, when I do a warm reboot, my computer just hangs for 30 minutes and then restarts, with the bios version still at A07. I am running Hardy 64bit, and the only thing I currently suspect as the cause of the problem is that my ext3 partition is journalized (rootflags=data=journal boot flag) which to my knowledge is unreversible since if I remove the bootflag the file system becomes read-only and I had to use live CD to fix it. Anyone with a similar experience and/or advice?

---

### Post by Lacrimstein on 2008-06-12
I tried manually upgrading with dellBiosUpdate command, but got the same results

---

### Post by Lacrimstein on 2008-06-12
I installed gutsy 32 bit on a different partition and upgraded from there.

---

### Post by OffHand on 2008-06-12
Too solve problems with your touchpad check this guide: [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530)

---

### Post by sdennie on 2008-06-12
I wasn't even aware it was possible to update the BIOS from linux.  I just updated my XPS m1330 to A10 and it worked fine (though, it scared me when I rebooted the machine and it just had fading in random colored vertical lines for a few seconds and then rebooted itself).  As a precaution, I turned the journaling on my root partition back to ordered (may not have been needed as I have a separate boot partition that is ext2) and it went smoothly.

Thanks.

---

### Post by Bezdomny on 2008-08-27
If you want to update the bios for M1530 or M1330 I have created a bootable CD that contains all bios updates for these two Dell's (plus a few other ones).

Stick the CD in the drive, boot from it.

When you get the prompt change to the CD drive, e.g D:

change directory into the dell folder then into the folder for the specific laptop.

Run the appropriate bios update.

The laptop reboots automatically when the update is finished.

Download the ISO from:

[http://www.eeebuntu.org/download/biosupdates.iso](http://www.eeebuntu.org/download/biosupdates.iso)

Burn the image to a CD.

---

### Post by Clockswork on 2008-10-19
> **Bezdomny said:**
> If you want to update the bios for M1530 or M1330 I have created a bootable CD that contains all bios updates for these two Dell's (plus a few other ones).

Stick the CD in the drive, boot from it.

When you get the prompt change to the CD drive, e.g D:

change directory into the dell folder then into the folder for the specific laptop.

Run the appropriate bios update.

The laptop reboots automatically when the update is finished.

Download the ISO from:

[http://www.eeebuntu.org/download/biosupdates.iso](http://www.eeebuntu.org/download/biosupdates.iso)

Burn the image to a CD.

Does this CD come with the A09 Bios for the m1530? And can someone confirm that this CD works? Thanks

---

### Post by Clockswork on 2008-10-19
Hello! I recently wrote a guide on how to upgrade your DELL bios in ubuntu. 

[COLOR="Red"]http://www.clockswork.org/?p=3 BROKEN[/COLOR]

Hope it helps!:popcorn:

---

### Post by chinoy on 2009-09-10
Can you help with my problem
[http://ubuntuforums.org/showthread.php?t=1262659&highlight=dellBiosUpdate](http://ubuntuforums.org/showthread.php?t=1262659&highlight=dellBiosUpdate)
Seems like its broken in the latest version !!!

---

