---
title: "Xubuntu Screen changes"
date: 2006-09-14
forum: Desktop Environments
---

### Post by jamesr on 2006-09-14
Hi ,

I am running Xubuntu 6.06, and suddenly my default screen has changed.Originally the screen had a toolbars at the top, showing applications and web browser icon and to the top right was a symbol where I clicked to shutdown.
Also at the bottom of the screen was another toolbar with the current processes and to the right, was the 4 workshpaces icons.

After rebooting the screen now shows no toolbars. The right click works the show the desktop menu. It seems as if there is a hide function enabled. But are far as I am aware I had not changed any settings. The only thing I had done to install Mondo and Mindi. Run Mondo arescue in root terminal window. Reboot to check out the CD created it did not work but that is another story. But it tried to boot. Now the boot to the disk shows the this screen problem.

---

### Post by jamesr on 2006-09-14
Hi,

A quick update with more information.

If I login with a new login after the screensaver prompt but as the same user (it is allowed, it even checks if that is what you want to do), the new screen is correctly displayed.

Also under the error conditions even the minimized icons are not see, their processes seem to be layered behind the current screen.

---

### Post by robc02 on 2007-01-16
I had the same problem on one of my families machines. I couldn't find out what had happened to cause it but managed to fix it.
I restarted x using control-alt-backspace and then logged in again BUT selected new xfce session under the Sessions button (bottom left of login screen). I think this is what did the trick but I also deleted a file called .cache-something-or-other. Unfortunately I can't remember the name of the file - I got the info off the forums after searching for something like "xfce toolbars" or "xubuntu toolbars". I will try to find it again and let you know.

---

