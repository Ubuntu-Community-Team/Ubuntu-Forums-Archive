---
title: "Cannot create bootable USB stick for Xubuntu"
date: 2013-07-01
forum: Desktop Environments
---

### Post by enverhoxha on 2013-07-01
I want to install Xubuntu from a USB stick. 
I downloaded versions 13.04 and 12.04, both 32 and 64 bits, and used Startup Disk Creator. Each time I got, after a while, an error message... about the checksum! 
I downloaded first from torrent, then from mirrors, but there's no difference. Every time the outcome is the same.
What can I do?

---

### Post by ajgreeny on 2013-07-01
When do you see the error; is it when you try to boot the USB or when you install to hard disk?  I am fairly sure there is a way to check the USB in the same way that you can check a CD or USB, but regret that I am not sure how you get to that first menu when using a USB; maybe you need to quickly press Esc or Shift or some other key.  Anyone - -?

If you downloaded using a torrent client, whether in Ubuntu or Windows, the .iso file must be good as torrents check packets as they are downloaded, so that points to either your USB drive as being faulty in some way (never heard of this problem happening, however) or your Startup-disk-creator not doing the job properly; something I have seen before.

See if you can use unetbootin to "write" the .iso file you already have to the USB to see if that helps your problem.

---

### Post by enverhoxha on 2013-07-01
I get the checksum message during the process of copying files to the stick. 
I click on "Make Startup Disk" in Disk Creator, the installation begins, files are being copied but, at some point (41% complete...), this stops and the "Checksums do not match" warning comes up. Mirror or torrent, 32 bit or 64 bit, 12.04 or 13.04 - it doesn't matter.

---

### Post by ajgreeny on 2013-07-01
Are you certain the USB has space?

---

### Post by enverhoxha on 2013-07-01
I've just bought the stick, 8 GB. I first tried it directly after unwrapping. Then I formatted it (FAT), just in case. 
Of course, the stick works. I can write to it. 
In fact, when i get the checksum message, most of the files are already on the stick...

---

### Post by ajgreeny on 2013-07-01
In that case I have no other ideas except for the unetbootin suggestion.

---

### Post by enverhoxha on 2013-07-02
Thanks. I will first try the same thing with Ubuntu, to see what happens.

---

### Post by sudodus on 2013-07-02
Try cloning the iso file to the USB stick with dd, and use a shell-script to help you finding the correct device, This method has a high success rate with Ubuntu family boot iso files. See this link: [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by enverhoxha on 2013-07-11
I downloaded an iso file for Xubuntu from another source (a newer version) and this time Disk Creator did the job. 
But my laptop did not boot from the USB stick. I got the message ”boot error".
The BIOS doesn't include the boot option USB flash drive. There are a couple of USB options - USB CD, USB hard disk... - but nothing about flash drive. 
If the stick is inserted, BIOS detects it - and displays the boot option "USB Hard Disk". Obviously this doesn't work with a flash drive.
Is there any way of using the stick to boot, other than replacing the BIOS (which I don't see how I could do myself)?

---

### Post by sudodus on 2013-07-11
Often a USB pendrive is 'seen' by the computer as a hard disk (actually a mass storage device). So 'USB hard disk' should be a good option.

Check also in another computer, if the USB drive is really working as a live or boot drive.

-o-

If you have a working CD/DVD drive, there are alternatives: either to make a CD/DVD boot drive from the Xubuntu iso file or to make a plop boot manager CD, that can install a USB driver, so that you can boot from the USB drive. See this link

[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

---

### Post by enverhoxha on 2013-07-11
Perhaps it matters that I have on my laptop 2 partitions (Windows and Ubuntu) with Grub. 
Normally when I start the computer Grub lets me choose the OS. Now if I insert the stick and then start the computer and select (F9) the option boot from USB hard disk, I don't get to the Grub screen anymore, I just get stuck with the "boot error" message. 

(What I want to do in the end with the stick is to install Xubuntu 12.04 on the old Ubuntu partition without a DVD.)

---

### Post by sudodus on 2013-07-11
No it does not matter that you have 2 (or several) laptop partitions.

When you boot from the USB drive, that drive has the focus. Try again with  'USB hard disk' as the first boot option in the BIOS menu.

---

