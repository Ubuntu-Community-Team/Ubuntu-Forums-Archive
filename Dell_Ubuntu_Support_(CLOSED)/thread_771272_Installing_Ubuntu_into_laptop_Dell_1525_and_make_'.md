---
title: "Installing Ubuntu into laptop Dell 1525 and make 'Media Direct' button work"
date: 2008-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by a2gs' on 2008-04-27
Hi,

I bought a laptop Dell 1525 (without Ubuntu, only Windows Vista). Now, I want put Ubuntu.

Please, how can i do to work with Dell Media Direct? (the house button)

I want to press 'Power On' and GRUB list Ubuntu or Windows to boot, and if I press 'Dell Media Direct' (the House button, when computer is off) the laptop startup and goes to Dell Media Direct screen.

Is it possible? And please, how can i do it?

I ALREADY installed Ubuntu with this partition schema:
/dev/sda1 - Dell Utility    (I did not touch in this partition)
/dev/sda2 - Linux           (I created this)
/dev/sda3 - Swap            (I created this)
/dev/sda4 - Win             (I created this)

Now, when the computer is off and I press the 'Dell Media Direct', a screen of Dell Media Direct comes, but after that, GRUB take the place and start the boot menu.

Please, how can i do to GRUB not starup when pressed 'Media Direct'?

ps: when ubuntu is loaded, if I press the house button cames to screen the app 'Music Player'. It is fine to me. I only want Media Direct screen when comupter is off, not GRUB.


Thanks a lot for help!

---

### Post by neptho on 2008-04-27
You can't; not easily.

Dell's Media Direct Button is a combination of BIOS, and a custom boot loader.  You'd have to put Dell's bootloader back at the beginning after dding a small image of Grub and saving onto your Vista partition, and all of the other changes.   I won't pretend I care enough to even try to do so, myself.  :)

---

### Post by atcmonke on 2008-04-28
I think it is easy because it's something I am trying to achieve right now if I understand him correctly:
MediaDirect = Linux, Power = Vista

Is this right? If so, could you please tell me how you got
this going?

Back to your problem though, you would have to boot into
Windows, run CMD as Admin, know which partition you are
going to be working with:
//diskpart > select disk 0, list partition, and it should tell
you //
after you find out which partition you are going to work with,
insert your Dell Media Direct disk in and run:
//X:\dellkit\rmbr.exe DELL Y Z//
replace X with your optical drive letter
replace Y with your Vista partition number
replace Z with your MediaDirect partition number

Hopefully you did not format your MediaDirect partition
because even if you are Dual Booting Vista/Ubuntu, the
MediaDirect button should have booted up MediaDirect and
not Grub.

You can trust me on what I say here because I have been spending
the past couple of days trying to get:
MediaDirect button = Ubuntu / Power button = Vista
with no success and broke my MBR many times but was able
to recover it. So if you have any similar problems, I may
be of help there. :)

---

### Post by ubun2008 on 2008-04-28
Hi,
I got it working perfectly.Please check this link
[http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html](http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html).

@a2gs.
If you had formatted your harddisk you can create a small new primary partition at the end and then put the media direct cd and reinstall..I hope it will work...had done it earlier..

---

### Post by atcmonke on 2008-04-29
i think the op wants to get MediaDirect = MediaDirect
rather than MediaDirect = grub

---

### Post by maccam94 on 2008-04-29
In order to have Media Direct work, the original bootloader must be restored, and then you must follow a guide like this to use the Windows bootloader: [http://www.oreilly.com/pub/h/2337](http://www.oreilly.com/pub/h/2337)
(you can skip from "ARC Disk and Partition Syntax for BIOS Drives" down to "Booting Linux")

---

### Post by ergosteur on 2008-12-05
> **ubun2008 said:**
> Hi,
I got it working perfectly.Please check this link
[http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html](http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html).

@a2gs.
If you had formatted your harddisk you can create a small new primary partition at the end and then put the media direct cd and reinstall..I hope it will work...had done it earlier..

I just bought an Inspiron 640m but don't have the MediaDirect CD. Where can I get that rmbr utility?

---

