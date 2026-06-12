---
title: "Openoffice Crashes, hardware issue?"
date: 2006-05-16
forum: Desktop Environments
---

### Post by BeachBum on 2006-05-16
Hello everyone,

I'm experiencing some very strange behavior with Open Office.  Anytime I try to use Open office (when I try to open .doc, .xls, .ppt, or .rtf, I never run OO from a command line or links), OO runs for a bit, then all of a sudden the hdd light on my laptop stays solid, and the hdd makes a rhythmic rotational noise thats too periodic and rhythmic to be random noise.  I try to continue using the computer and slowly applications do not respond and the computer ultimately freezes.  Pressing ctrl+alt+backspace takes me to a blank black screen, and the only way to use the computer is to give it a hard boot. Until I reboot, the harddrive continues to make the same periodic noise and the hdd light is solid.  

I only experience this behavior with OO and no other applications.  This occurs in both KDE and Gnome, with all updates and the added repos.  OO is version 2.01-breezy1.  Laptop is Thinkpad T42.  Checking system logs shows only one unusual entry:

[4294672.948000] hdc: UJDA755yDVD/CDRW, ATAPI CD/DVD-ROM drive
[4294675.668000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294784.416000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294784.416000] hdc: drive_cmd: error=0x04 { AbortedCommand }

My computer and OO have a history of these errors.  Occasionally, I'll open a document (most recently was a .ppt), and it displays everything fine and starts up fine and I can navigate the ppt, however it randomly freezes with the rhythmic harddrive noises.  Upon a hard reboot, the boot process stops at mounting hard drives, the noise starts up, the hdd light goes solid, and the error above (DriveReady SeekComplete Error) comes up repeatedly, synchronously with the rhythm of the harddrive.  The computer refuses to boot, (continues to display these errors) so I take out my trusty Debian cd, run e2fsck on the partition, and boot normally back into Ubuntu as if it never happened.  I'd be convinced this is a hardware glitch, however I have Windows on this computer as well and when the moon is blue and I boot into it, I have no problems at all.  

So any ideas?  Any worthy subsitutions for OO?  (Kword doesn't display pictures and formatting in most of my collaborated docs, Abiword locks up occasionally but displays everything correctly, and Gnumeric is descent, but gtk + kde is not very pretty...)  Is there a way to uninstall OO and reinstall from the latest sources?  

Thanks for all input!

---

### Post by link141 on 2006-05-16
Open Office is a huge complicated package, in which many errors can occur.  My guess is that due to a bug in the application, or missing files the program runs through an endless loop performing some hard drive operation.  Unfortunately, I do not have much back ground knowledge in this area.  Maybe this bug will be resolved if you decide to switch to the Dapper stable when it becomes available.  Thanks for reading my post :).

---

### Post by BeachBum on 2006-05-16
Thanks for the reply.

I did a little more snooping around and ran some SMART programs (smartctl and Hitatchi's Drive Fitness Test (bootable ISO for IBM's harddrives)) and discovered possible impending failure.  Running the Hitatchi diagnostic told me I had bad sectors and when I attempted to fix them, it told me half way through that it could not and the device is faulty.  I will be in contact with IBM to get a replacement.

Though I don't understand why OO does this, and no other apps.

---

### Post by megabyte405 on 2006-05-26
It could be the physical location of the program on the hard drive.

Not sure why your CD-ROM drive is throwing errors when your hard drive is failing, but I'm glad you found the problem.  Hard drive corruption (even just minor filesystem things) can cause some frustrating troubles in any OS (recently had some bad luck with Windows and these sorts of issues).

Thanks for trying AbiWord, by the way!

-- Ryan, AbiWord Dev and Win32 Maintainer

---

