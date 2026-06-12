---
title: "Latitude Nvidia drivers &quot;turn off&quot; display"
date: 2007-11-24
forum: Dell  Ubuntu Support
---

### Post by Xixor5000 on 2007-11-24
So I installed ubuntu on my dell latitude without problems and everything was working fine until i enabled "advanced desktop settings"...at this point it downloaded the updated nvidia drivers and asked for a reboot which I did, everything loads fine until the login screen when the monitor actually turns off...the computer is still on though because i can login with the keyboard and hear the ubuntu sound, etc.

So I booted into recovery mode and now am looking at a terminal command prompt where I have absolutley no clue as to what to input to attempt to uninstall those new drivers, if anyonw has any idea as to how to proceed it would be appreciated because if not i am going to have to completely reinstall the operating system again and start from scratch...

---

### Post by Jumpmasterrt on 2007-11-25
It may not be any consolation, but the same thing happened to me on my 4700 desktop with an ATI card... I'm sitll looking for a solution.

---

### Post by nick_h on 2007-11-25
Edit the file /etc/X11/xorg.conf using:
```
nano /etc/X11/xorg.conf
```
(or use vi as an editor if you prefer)
Find the line:
```
Driver          "nvidia"
```
and change "nvidia" to "nv".

This should get you back to a working system.  Then you will have to work out why the new drivers didn't work.

---

