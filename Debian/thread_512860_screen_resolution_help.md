---
title: "screen resolution help"
date: 2007-07-29
forum: Debian
---

### Post by dynoweb on 2007-07-29
I am using Debian4.0 and the resolution at install is 640x480 this is way weird....
I need to get the resolution to 1024x768 does anyone know how?

---

### Post by Pobega on 2007-07-30
Have you tried *dpkg-reconfigure xserver-xorg*?

---

### Post by dynoweb on 2007-07-30
> **Pobega said:**
> Have you tried *dpkg-reconfigure xserver-xorg*?

if i knew what you were talking about I could answer that.... I am new to debian and I keep getting the run around about everything i post on this forum.
The resolution i have is 640x480 I have lines on my screen.... it looks like crap I can barely see the screen. I need to have 1024x768 for this screen. I am running a dell latitude c600 it was running windoze 2000 on it, and I changed it to Debian and want to keep Debian4.0 if someone knows what the hell they are doing please post in this forum and help me and others that might have the same problem.

Thank you

---

### Post by tommcd on 2007-07-31
Do this:
1)boot up debian in recovery mode from the grub menu, or boot up to the desktop, hit ctrl+alt+F2, login as root, and run "/etc/init.d/gdm stop".
2) still as root, run "dpkg-reconfigure xserver-xorg". Choose defaults for all options if you don't know them. when you get to the monitor section, choose advanced and enter the desired resolution (select with space bar), and enter the monitors horizontal and vertical refresh rates. Or choose medium and just select the screen resolutions if you don't know the horizontal and vertical refresh rates.
3)after completing this just type "reboot" and hit enter. Your screen resolution should be good.

This is the same way screen resolutions are fixed in ubuntu.

---

