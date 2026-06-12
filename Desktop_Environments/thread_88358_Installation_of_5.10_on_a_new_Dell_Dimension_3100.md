---
title: "Installation of 5.10 on a new Dell Dimension 3100"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Diaboblop on 2005-11-10
I've got Ubuntu running on my other computers fine, but am having trouble installing Ubuntu on my new Intel 4 machine.

What happens is that I boot from the CD and then press Enter.

I then get loads of messages like

uhci_hcd : host system error, PCI Problems?
uhci_hcd : host system fail.

The last thing that appears on screen is

Starting system daemon syslogd, klogd [ok]

at this point the computer freezes and will not motion any further
I have tried the linux aic7xxx=no_probe command and still no go.

Anyone got any suggestions for me to try?
Cheers all
Chris

---

### Post by Diaboblop on 2005-11-13
I've managed to get Fedora Core 4 installed on the computer without any sort of tweaking.  But I really want to put Ubuntu on there.

Is there anything I could do, whether it's a long way round or whatever.

---

### Post by kelsey23 on 2005-11-13
Well first of all, every Dell I have used has been crap. I don't know why, a PC is a PC, but they just don't seem to be as good as some of the other OEMs. It could be a hardware issue. If that was me, I would re-install at least one or even maybe two more times, it is possible there was an error in the install. You can also try to install Debian, and see if that works. If it won't install, then most likely you aren't going to get Debian to install, either.

---

### Post by nix4me on 2005-11-13
Thats a dumb response.

Alot of us use dells with Ubuntu and Linux and have no problems.

nix4me

---

### Post by Diaboblop on 2005-11-13
Debian wouldn't install either, it kept informing me that there wasn't a hard drive attached to the computer.

This happened in the partition disks stage.

---

### Post by Pathfinder73 on 2005-11-14
Hi

I'm getting the exact same error on a brand new Dell Dimension 3100.  

The error reads:

uhci_hcd 0000:00:1d.1: host controller process error, something bad happened!
uhci_hcd 0000:00:1d.1: host controller halted, very bad!

This error occurs following booting from the Breezy CD and I've tried and got the same error using a Hoary Live i386 CD.

Any thoughts?

Thanks in advance.

---

### Post by Diaboblop on 2005-11-15
I'm going through the distributions slowly to see if I can spot why Ubuntu won't install.

KNOPPIX comes back with a no hard drive attached error message
Gentoo, gets to the command prompt for root, but when I run fdisk or cfdisk the only drive I am able to see is the CD-ROM drive.

What version Kernel supports SATA?

---

### Post by NeoChaosX on 2005-11-15
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by Pathfinder73 on 2005-11-15
Thanks for the link NeoChaosX as it made for an interesting read and I assume that is what my problem is.  Unfortuately, I am so much of a linux newbie that I wouldn't dare try any of the work arounds - yet.  Luckily, I have another computer on which Ubuntu runs beautifully.

---

### Post by dhpeterson on 2005-11-23
I have exactly the same issue on a Dell Dimension 3100 here. I can confirm that the breezy installer, hoary installer and hoary live cd all experience the problem.

What is the role of uhci_hcd? Is it related to the SATA chipset as the link posted by a previous respondant implied?

Any news from other users on a workaround?

--Dave

---

### Post by RAOF on 2005-11-23
You might have better luck in the [Installation & Upgrade forum]("http://www.ubuntuforums.org/forumdisplay.php?f=94"), but you could try booting with something like: "linux noacpi apci=off"

Edit: Oh, and uhci is a part of the USB subsystem, I think.

---

### Post by dhpeterson on 2005-11-23
Follow-up: I am able to boot successfully using Knoppix 2.6 !!

From the output of lspci, I have determined that the USB controller on the machine is a 82801FB/FM/FR/FW/FRW (IHC6 Family).

Four UHCI controllers are successfully detected:

0000:00.1d.0 -> UHCI #1
0000:00.1d.1 -> UHCI #2
0000:00.1d.2 -> UHCI #3
0000:00.1d.3 -> UHCI #4

One other point of interest in lspci output is "Ethernet controller ... Unknown device 1064 (rev 04)". Looks like Knoppix at least doesn't know about the ethernet controller. I haven't tested networking yet so I don't know if this a problem.

My main question is this:

What's different about the kernel in Knoppix 2.6 vs. the ubuntu kernel  that allows knoppix to boot successfully when ubuntu does not?


--Dave

---

### Post by dhpeterson on 2005-11-23
[QUOTE=RAOF]You might have better luck in the [Installation & Upgrade forum]("http://www.ubuntuforums.org/forumdisplay.php?f=94"), but you could try booting with something like: "linux noacpi apci=off"

Edit: Oh, and uhci is a part of the USB subsystem, I think.[/QUOTE]

Yes, quite right. This is why I was confused by the previous link to the URL on SATA. A red herring, I think!

The SATA drive is being detected fine by both ubuntu and knoppix. The problem does not lie here, but rather with the USB chipset, it seems.

I will try the installation forum, thanks for the tip.

--Dave

---

