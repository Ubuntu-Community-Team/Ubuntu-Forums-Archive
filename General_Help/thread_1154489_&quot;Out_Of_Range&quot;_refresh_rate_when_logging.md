---
title: "&quot;Out Of Range&quot; refresh rate when logging in?!"
date: 2009-05-09
forum: General Help
---

### Post by nightfire117 on 2009-05-09
Must've selected the wrong resolution or messed with my xorg.conf. I reset that using the command to return to default xorg.conf many times, uninstalled, reinstalled nvidia drivers. Thing is, every time I boot I get to GDM just fine and log in. Then my monitor says "OUT OF RANGE".

When I reconfigure xorg.conf to default, it works without enabling my nvidia drivers (tried using 93, 173, 180 - all give this problem). So once I reinstall + "Activate" those drivers in the Hardware Configuration thing (where you activate/install proprietary drivers), and reboot, suddenly this problem comes up again.

I can log into Fluxbox just fine, but I want Gnome to work and if my nvidia drivers don't work in Gnome who's to say they'll work in Fluxbox?

Using Ubuntu 8.10, this problem came up. Upgraded to 9.04 to see if it would fix it but naw. I don't really wanna do a clean install, but I might.... :(

Comp specs: 1.5 GB RAM DDR 2; Pentium 4 3.06 GHz; Ubuntu 9.04 32-bit (with Windows 7 on another hard drive, irrelevant).

Thank you for any help. I've tried many threads, and some of them are old, but I've tried *everything* - please help? You guys always come through XD

~Night

---

### Post by dcstar on 2009-05-09
> **nightfire117 said:**
> Must've selected the wrong resolution or messed with my xorg.conf. I reset that using the command to return to default xorg.conf many times, uninstalled, reinstalled nvidia drivers. Thing is, every time I boot I get to GDM just fine and log in. Then my monitor says "OUT OF RANGE".

When I reconfigure xorg.conf to default, it works without enabling my nvidia drivers (tried using 93, 173, 180 - all give this problem). So once I reinstall + "Activate" those drivers in the Hardware Configuration thing (where you activate/install proprietary drivers), and reboot, suddenly this problem comes up again.
.......

Delete any (hidden) .nvidia files in your home folder.

---

### Post by nightfire117 on 2009-05-09
Will try, then edit this post to tell you how it goes.

~Night

[EDIT]: Enabled viewing of hidden files (in Thunar) but to no avail - there's no "hidden" .nvidia files, folders, or anything in /home/my_username_here and no hidden files/folders period in /home/.

~Night

---

### Post by nightfire117 on 2009-05-12
Bump - no progress...! Please help, someone?

I'm considering a fresh install, maybe even Fedora Core 10... just want to get this working without an install seeing as I have my setup the way I want it and with all my programs, plugins, codecs, etc...

~Night

---

