---
title: "Boot problem, possibly grub, &quot;crc error&quot;"
date: 2009-05-03
forum: General Help
---

### Post by adamfaulkner1 on 2009-05-03
Greetings.

When I boot my computer, nothing out of the ordinary happens until I get the "Grub loading stage 1.5". At this point, it hangs for about 15 seconds, then shows the "Press escape to enter the menu". After this stage, I see "booting yadayada root= yada yada..."
All normal.

Then I get "Undefined Video Mode ???? Press Enter to see possibilities, or press space to continue". If I press Enter I am presented with a plethora of video modes, but no matter which I choose, I immediately get an error message that says "crc error". I must reboot. This also happens if I press space.

I have had this problem across 3 different distros (Debian, Gentoo, Ubuntu). I have also had a somewhat similar problem with the OpenSolaris install disk, which uses grub. My current workaround is to use SYSLINUX on a usb drive and to copy the kernel and initrd to it. This is un-preferable because I must constantly have a usb drive plugged into my machine, and when apt updates the kernel, I must manually copy it to the usb drive.

FreeBSD and Windows can boot perfectly with their respective boot managers.

I have tried updateing the bios to the latest version, and I have tried using LILO. Lilo doesn't get past the "L" (i'm not really sure what that means).

I believe this is a problem with grub because {sys,iso}linux bootloaders can load perfectly, and the Windows and FreeBSD bootloaders have no problem with it.

Does anyone have any ideas? I am open to replacing the bootloader.

I have an intel D945GNT motherboard. This occurs across different hard drives.

Thanks.

---

### Post by adamfaulkner1 on 2009-05-03
I might also mention that the Debian "Etch" 2.4 kernel booted great after a few obscure errors.

I will attach a dmesg if it helps anyone.

---

### Post by adamfaulkner1 on 2009-05-05
I believe that this problem may be caused by the kernel and my hardware. Again, I have an intel D945GNT board, and an NVidia pcie graphics card. It complains about display immediately prior to glitch.

I tried compiling another kernel with all the nvidia stuff in there not as modules, but that didn't do anything. I get this weird message with my current setup:

ata1.00: status {DRDY ERR}
ata1.00: error {ICRC ABRT}

Will try googling this stuff.

---

### Post by cariboo on 2009-05-05
That looks more like a hard drive error, than a video driver problem. I would suggest you go to the hard drives manaufcaturers web site and download and use the tools on the hard drive. If you have the problem across three different distros, I would start looking at hardware problems.

---

### Post by adamfaulkner1 on 2009-05-06
Thats what I would think from just google searches, but this error occurs across 3 hard drives that work perfectly using bsd. This error also occured on the OpenSolaris install disk, which uses grub as the bootloader. My DVD drive and hard drive are on the same ide cable, so it might be an error with that part of the system.

The Bios also has many options regarding hard drives. It has Legacy Mode, Serial or Something else, enhanced mode, SATA something. I have tried many permutations of these options, but every time I change one grub hangs while it's loading stage 1.5. It also does this if i remove my DVD drive.

Any ideas? What mode should I put the bios in? I have tried reinstalling grub, but this won't work

Thanks.

---

### Post by adamfaulkner1 on 2009-05-06
WOOHOO! Fixed it! 

It was a bad cable. Salvaged another one from one of my machines, works great! Thanks!

---

