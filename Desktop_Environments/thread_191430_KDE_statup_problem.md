---
title: "KDE statup problem"
date: 2006-06-07
forum: Desktop Environments
---

### Post by shugie on 2006-06-07
On startup my KDE refuses to start. I have NVIDIA drivers installed so I see the NVIDIA startup screen and am able to use a mouse, but before the logon screen appears I end up either logging into the command line, or not being able to login at all. Then I keep getting an error about not being able to load "bcm43xx_microcode5.fw". It seems that is related to a wireless driver, but my wireless has never working under linux, so I don't think that is a real problem. Is there a way to reinstall KDE and have it startup through the recovery console? Preferably a way to repair KDE because I would like to retain the packages I already have installed.

Thanks

---

### Post by tonyr on 2006-06-07
Try this when you can log in at the command line. Edit the file /etc/X11/xorg.conf.
find the line that says **Section "Device"**.  That's the video device driver definition
section.  Comment out the line (with #) that starts with
**Driver**, add a new line that says **Driver   "vesa"**, save and reboot.  That 
might get you to a minimal working X session, and you can explore further mods then.

---

### Post by shugie on 2006-06-07
That didn't work. It still brought up my mouse for a minute, then cut back out as if KDE doesn't want to start. Any other ideas?

---

### Post by tonyr on 2006-06-07
The file **/var/log/Xorg.0.log** shows what happened during X startup, and may shed
some light on what exactly is failing.  Look at that and post it here if you can.  Post
your xorg.conf too, if possible.

---

### Post by shugie on 2006-06-07
The file contains no (EE) or (WW) or (??) labled lines in the files. Can you tell me which lines would be most helpful because the file is quite long and probably not postable. I also keep all of my valuable information in another partition, so I'm not too worried if the easiest solution is somehow reinstalling KDE if that is the problem. As long as I only have to change a few settings and don't have to install everything again I would be fine with a fresh KDE.

---

### Post by tonyr on 2006-06-07
You could compress the file and attach it (paper clip icon in the tool bar above).  I'll attach
mine here for comparison.  The interesting lines are those that start with **LoadModule**,
and the few lines that follow, especially the ones about the video driver. The last lines
are of interest, also.

---

### Post by shugie on 2006-06-08
Here are the files. Nothing looks too different from yours. Could it be something after X starts?

---

### Post by tonyr on 2006-06-09
I think it has to do with your display dimension, which is defined in your **xorg.conf**
file as **1680x1050**.  There is much discussion in these forums about this issue.
I don't have the time right now to do the search.  You can use search terms 
**resolution**, **display**, **nvidia**, alone or in combination in the
Advanced Search item under the Search menu.  I'll try to get back to this tomorrow.

---

