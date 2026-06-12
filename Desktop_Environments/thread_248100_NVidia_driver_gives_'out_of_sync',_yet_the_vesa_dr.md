---
title: "NVidia driver gives 'out of sync', yet the vesa driver works fine?!"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Ribs on 2006-08-31
Hi,

I'm trying to set up a MythTV home PVR system using some old computer bits I've just got hold of, and I've stumbled upon a rather strange problem...

My TV has a VGA input which it can take directly from a computer. This is better than using a S-VIDEO to SCART cable, as the picture is crystal clear, and there is no interferance.

However, when using the NVidia driver for the FX5200 graphics card in the machine, my TV goes crazy, kills the screen and puts a "out of sync" message in the middle of the screen.

But, when using the vesa driver, and all other parts of the x.org file being equal, I find that the TV works perfectly.

I only found the vesa driver working when I tested the Ubuntu LiveCD, and found the display to be perfect using the vesa driver. Gnome reported a display of 1280x1024@85hz in the LiveCD session.

Why does the vesa driver work perfectly, and yet the nvidia driver cause problems when the rest of the xorg.conf file is identical (except the driver part)?

Attached is my xorg.conf file... it's pretty standard, I think you'll agree.

Any help would be fantastic right now, a slow vesa display isn't much help for a MythTV PVR box...

---

