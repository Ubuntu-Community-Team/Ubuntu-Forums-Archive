---
title: "Hybrid 32 and 64bit Install DVD"
date: 2010-12-04
forum: Development CD/DVD Image Testing
---

### Post by TechWiz2100 on 2010-12-04
Hey guys, didn't really know where to post this so mods feel free to move if necessary.

Anyway, I was just wondering, since Ubuntu install CDs are, well, CDs (just shy of 700MB), why hasnt anyone created a DVD that is a hybrid for 32bit and 64bit installs? I mean it makes perfect sense that if it fits on a CD, then you can fit multiple distro's on 1 DVD and the 64bit kernel can tell you that it can't load on the current system.

And just before you guys go out saying its not possible because of the architectures are incompatible and all that stuff, look at OS X which has a 32bit flag for its DVD setup.

Just throwing this out there

---

### Post by TechWiz2100 on 2011-01-18
bump?

Anyone feel like giving this a go?

I'm sure grub could load a script that checks which version is compatible and load the proper installer. Maybe a multi-part DVD? I don't really know, I'm just throwing out ideas here.

---

### Post by pjman on 2011-01-21
I know it's not the same, but you can try tools that allow you pick which ISO to boot off of from a USB drive. Here's one:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

**UPDATE**

Here's another one - [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by TechWiz2100 on 2011-01-21
Hmm, I might be able to do something with this an that CD remastering program... thanks for the link pjman

---

### Post by oldfred on 2011-01-21
I manually created my multiboot USB. The scripts make it easier to create the correct grub.cfg boot stanzas for each install. I had thought about something similar but now find USB so easy, I do not use CDs hardly at all anymore.

But you could combine the USB grub multiboot and grub on a Cd/DVD.

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)


ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

