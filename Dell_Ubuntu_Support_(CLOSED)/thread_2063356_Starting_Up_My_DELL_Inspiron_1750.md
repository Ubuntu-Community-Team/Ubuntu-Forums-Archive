---
title: "Starting Up My DELL Inspiron 1750"
date: 2012-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kaamady on 2012-09-26
Hi, I created a bootable usb stick with ubuntu 12.04 LTS to install on my computer alongside windows. It installed perfectly, and everything works great, except for my wireless card (working on that). But when I restart my computer, it automaticly boots into Windows 7. I have to plug in that  bootable usb drive and hit f12 and then select usb drive to get to grub to boot linux... I want Grub to open at start up and ask weather i want Linux or windows to boot, every time I start up. I won't always be able to boot with the flash drive.... Need Help On This!

---

### Post by mikewhatever on 2012-09-26
It looks like GRUB got somehow installed to the USB drive, but that should be easily fixable. Boot Ubuntu with the USB drive plugged in, and then disconnect it. Open a terminal window and run

```
sudo grub-install /dev/sda
```

/dev/sda should be the internal hdd's MBR.

Hope that works.

---

### Post by kaamady on 2012-09-26
This is what I get :(

sudo grub-install /dev/sda
[sudo] password for ******: 
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

---

### Post by kaamady on 2012-09-26
Nevermind, the way the string of words came up, it looked like it didn't install, but i tried to reboot, and it worked perfectly :D

Is there any way to hide grub on startup? Like have to press a certain button for grub to activate?

---

### Post by mikewhatever on 2012-09-27
Yes, GRUB menu can be hidden. Run 

```
gksudo gedit /etc/default/grub
```

and make the following two lines look like this

```
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
```

save and exit, then run 'sudo update-grub'.

You'll have 5 seconds to hit a Shift key after the BIOS screen to get the menu shown.

---

