---
title: "Correct Way to Switch from SATA AHCI to SATA 'IDE'"
date: 2009-04-18
forum: General Help
---

### Post by gmjs on 2009-04-18
Hi,

I have recently upgraded my Windows operating system to Windows XP, but had installed Vista alongside Ubuntu 8.04 with the SATA drives operating with the AHCI interface.  I couldn't get Windows XP to install, even with the required drivers for it to recognise the AHCI HDD interface, so I returned to IDE compatibility mode.

Ubuntu then, of course, couldn't start.  Unfortunately, I'm not an expert with the GRUB boot loader and loading kernel modules, so I added the line 'generic.all_geneic_ide=1' (documented in the help on the Live CD) as a kernel boot parameter to try and get it to recognise the HDD again.

This does work and all seems to be fine, but every time Ubuntu boots it prints the following before booting normally:

```
[0000...] Unrecognised boot option 'generic.all_generic_ide=1'; ignoring
```

Obviously, Ubuntu is not ignoring this option, as it doesn't start without it!  I'm obviously doing something wrong therefore, and wondered if anyone knows the correct way (besides reinstalling Ubuntu) to inform the kernel that I've switched HDD interfaces.

Picky, I know, but I like to know how things are supposed to be done!

Many thanks,

Graham

---

### Post by dasunst3r on 2009-04-18
If you have the drivers for your SATA controller, you should indeed install Windows XP using SATA IDE mode.  Afterwards, go into device manager and install the drivers for your SATA controller.  If things work out (i.e. no more exclamation marks or unknown devices), then you can change things back to the SATA AHCI mode.  However, if your Windows installation blue-screens on boot, then I'm afraid that you'll have to use SATA IDE mode all the time.

---

