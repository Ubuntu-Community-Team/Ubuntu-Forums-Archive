---
title: "Eject button fails on DVD/CD drive"
date: 2005-11-20
forum: Desktop Environments
---

### Post by tbe on 2005-11-20
Hi,
I'm dual booting Ubuntu with Windows XP on a TravelMate 290LMi, which comes with a CD/DVD writer.  Everything works fine, but when using Ubuntu, the eject button on the DVD drive does not respond - I have to do this manually either from the command line or from the desktop.

Is there away of re-enabling the eject button - it works OK under Windows XP

TIA,
tbe

---

### Post by invalid on 2005-11-20
Are you trying to eject while the disc is mounted? If so, it will prevent you from doing so, which will prevent data damage. It must be unmounted for the actual button to work.

Cb

---

### Post by RAOF on 2005-11-20
I don't think so.  The reason being, linux mounts the cdrom filesystem and thence forward assumes that the disc is available.  It might be possible to catch the eject button press in software, and automatically unmount/eject the disc, but I don't know of anything that does it.

---

### Post by teaker1s on 2005-11-20
you can setup a shortcut in gnome keyboard shortcuts and eject seems to work better than disk mounter or eject button on mine for stubborn drive

---

### Post by quietglow on 2005-11-20
right click on the disc in gnome and "eject" is in the popup menu.

---

### Post by matthewv on 2005-11-20
[QUOTE=quietglow]right click on the disc in gnome and "eject" is in the popup menu.[/QUOTE]
I have the same problem on a desktop as the original poster. The solution above works, but it's still nice to be able to use the eject button.

---

