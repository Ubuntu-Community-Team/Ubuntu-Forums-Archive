---
title: "Boot-up directly to console"
date: 2009-06-12
forum: General Help
---

### Post by qajaq on 2009-06-12
I would like to set up my Kubuntu 9.04 server to boot directly to a multi-user console, no desktop environment. In most flavors of Linux, other than the Ubuntu/Debian family, this would be runlevel 3. In the Ubuntu/Debian family, however, all runlevels from 2 through 5 are the same -- they run the GUI desktop.

In openSUSE and in Fedora I've been able to boot directly to a console simply by editing the inittab file; however, the Ubuntu family appears not to use inittab.

I've seen instructions to ```
mv /etc/rc3.d/S30kdm /etc/rc3.d/K70kdm
``` (in order to suppress calling KDE when booting at runlevel 3) and to add the digit 3 at the end of the "kernel" line in /boot/grub/menu.lst in order to boot at runlevel 3.

I have done both of those things. The first one appears to work. If I run the command 'init 3' the machine logs off the GUI desktop and asks me to log on the console. But when I re-boot, I am put into runlevel 2, not 3.

Do I need to add something other than simply the digit 3 at the end of the Grub's "kernel" line? Or is there something else I should do in order to boot to runlevel 3?

---

### Post by qajaq on 2009-06-13
The issue appears to have resolved itself after the machine was shut off overnight.

This is similar to the resolution of a problem I had recently when setting up a RAID-1 on this Kubuntu machine. In both cases, no matter how often I rebooted, the changes would not take effect. But when I shut the machine down overnight and re-started it in the morning, the changes were accomplished.

I am beginning to suspect that, at least in Ubuntu, a simple reboot may not be exactly the same as a complete shutdown and restart.

---

### Post by gradinaruvasile on 2009-06-13
If u remove the gdm (in your case kdm i think) package u will have the console login...

---

