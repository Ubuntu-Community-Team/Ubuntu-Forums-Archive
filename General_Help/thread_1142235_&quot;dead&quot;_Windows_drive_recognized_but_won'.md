---
title: "&quot;dead&quot; Windows drive recognized but won't mount (via USB)"
date: 2009-04-29
forum: General Help
---

### Post by MrSamsa42 on 2009-04-29
Long story, but I'll be brief...
A 160GB Hitachi Deskstar was my primary HD, booting Vista.  After a few spontaneous re-boots and BSODs, it apparently died.  Not only wouldn't Windows boot, but the BIOS refused to recognize the drive. Connecting to a second Windows (XP) machine via an USB enclosure got me nowhere -- refused to recognize it.  I wrote it off as a loss and tossed the drive in a drawer.  Months later, after coming to my senses and forsaking Windows for Linux, I decided to try again.  Jaunty recognized it right away, presenting an encouraging "USB Drive" icon in the File Browser, but it cannot be accessed.  I get the usual, "Unable to Mount to Location" message when I click on it.  I followed the directions in this thread:

   [http://ubuntuforums.org/showthread.php?t=1067393](http://ubuntuforums.org/showthread.php?t=1067393)

but I get, "special device /dev/sdb1 does not exist" when I try to force mount.  So, was my first assessment correct?  Is this drive hopelessly lost?  Thanks in advance for whatever help you might offer.

---

### Post by regor210 on 2009-04-29
There  are some instructions on mounting NTFS here.

 4.16

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Manually_Mount_and_Unmount_a_device](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Manually_Mount_and_Unmount_a_device)

Mounting NTFS Partitions (with read/write privileges)

---

