---
title: "noob: Reboot just Gnome? or partial re-boot?"
date: 2009-05-27
forum: General Help
---

### Post by jorx on 2009-05-27
Hi everyone,
I was wondering- I'm running Ultimate Ubuntu off of a USB jump-drive- however my system's BIOS only detects the jump drive as bootable on every second bootup.

Which means- when I tell it to use "Nvidia driver 177", it says "reboot your computer to use the new driver".
But rebooting does nothing, I can retry- and it'll say "reboot" even though I just did!

So is there a way to reboot the computer partially, or to reboot Xwindows, or Gnome, etc.?
I'm not sure how to use "init", but is there any other ways?
Or to tell the driver to load properly on startup?

It worked once for me, so I know it's possible. 

Thanks for your time!

---

### Post by Yellow Pasque on 2009-05-27
IIRC, logging out of GNOME will restart X. To manually restart X, add this to your /etc/X11/xorg.conf (or just add the 'Option' line if you already have a Serverflags section):
```
Section "ServerFlags"
        Option     "DontZap"       "false"
EndSection
```
Now you can restart X with Ctrl+Alt+Backspace (make sure you save your work first and close as much as you can).

---

