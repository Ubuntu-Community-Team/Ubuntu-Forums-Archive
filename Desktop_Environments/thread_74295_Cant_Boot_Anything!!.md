---
title: "Cant Boot Anything!!"
date: 2005-10-11
forum: Desktop Environments
---

### Post by astronerd on 2005-10-11
PLEASE HELP!  I came back to my computer after having left for a whle and I got a bunch of errors saying that I couldnt open or do pretty much anything cause it was read only.  I rebooted and during shutdown it gave me a ton of errors saying about read only read only(they were going too fast to remember specfics)  When I rebooted and got to grub menu, I chose normal 2.6.10-5-686 kernel and it starts booting, till it gets to ata2: disabling port.  Then it says
EXT3-fs error (device sda5) : ext3_get_inode_loc: unable to read inode block - innode=7209167, block=14417933
EXT3-fs error (device sda5) : ext3_get_inode_loc: unable to read inode block - innode=7209099, block=14417931
* no inittab file found

Enter run level: 

If I pick runlevel 5 or 6 it says no more processes at this run level and just hangs.

Then I do a hard reboot at after picking the same kernel it gives me an error saying
Error 18: Selected Cylinder exceeds maximum supported by BIOS. 
Press any key to continue.....

And if I pick 386, or XP(running dual boot), or recovery for any it still gives me error.  So basically I cant boot into anything.  Please help, i am a noob still so I dont know what to do.  I just did an upgrade today(not to breezy, just a regular upgrade that had some new kernel images and two other things) running hoary stable for a few months with no major probs..  ANY HELP PLEASE!!  Thanks

---

### Post by KingBahamut on 2005-10-11
Bad drive or a bad partition most likely. Specially if you cant boot into windows.  During the grub install most likely, However based on the BIOS error Id lean towards it being a bad logic board on the drive. How big is the hard drive? what are your system specs? 

You can attempt a reinstall of Ubuntu , and see if grub installs properly on the 2nd try , but if it doesnt , id blame the hardware.

---

### Post by astronerd on 2005-10-11
Well it has been running fine for a while, why would it just crap out during a session?  I have a 160 Gb hard drive, split with 20Gb for windows, 60 for Linux, and another 60 is free.  I havent done anything new or rebooted in a week or so.  I mean is there anything else I can try to test and see if I can fix this?  I just hate to reinstall and lose everything.

---

### Post by KingBahamut on 2005-10-11
You can grab a live cd , boot it, mount you linux part and do some testing that way. The inode errors speak of either a bad cable, bad controller, or a bad drive. Im assuming its an IDE and not SCSI.

---

### Post by astronerd on 2005-10-11
Sorry, I wouldnt know what to do with a live CD or what kind of tests to run.  Any suggestions?(sorry, noob here)  If I reinstall, whats to stop this from happening again?  I wanted to eventually get rid of Windows and keep linux as my sole OS, but I kept win. around in case something bad happened(like this) and I needed to boot into that.  Is there some way to prevent or help fix this so that it doesnt happen in the future?

---

### Post by astronerd on 2005-10-11
Well after a hard reboot, I picked XP from the grub menu and it did a checkdisk thing, then rebooted and I can now boot into windows.  Is this a good sign?

---

### Post by Ampersand on 2005-10-11
A Live CD is a copy of Linux installed on a CD, allowing you to run Linux without having to install it. If you go to [http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/) and download the Intel x86 live CD, you can burn it onto a CD and boot from it in the same way as you did with the installation CD. You can then open a terminal and run ```
sudo fsck
```.

---

### Post by astronerd on 2005-10-11
I think I have an old copy of knoppix, will that work as a live CD?  And after I enter fsck what do I do/look for?  I really have no idea what to do so please bear with me....Sorry!

Whoops, no I dont have a copy.

---

### Post by Ampersand on 2005-10-11
yep, Knoppix should work. Fsck (file system check) works in the same way as the windows disk scanner - it'll scan your linux partition and try and repair any problems it finds. It doesn't require much in the way of intervention.

---

### Post by euphonic05 on 2007-07-02
I have a similar problem. Its starts to boot, but the fsck starts and reports an error in sda5. It asks for my root password, which as far as I can tell is correct. But it does not accept it. Ive tried various methods of recovering my root password using Knoppix. I keep getting stuck. My windows partition works fine. I'm wondering if it would be easier to just reinstall. Im using Ubuntu Feisty fawn on a dell inspiron. I'm also very new to Linux. PLEASE ADVISE.Thanks.

---

