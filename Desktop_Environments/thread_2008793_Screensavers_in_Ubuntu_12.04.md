---
title: "Screensavers in Ubuntu 12.04"
date: 2012-06-23
forum: Desktop Environments
---

### Post by le_phoceen on 2012-06-23
Hi everyone,

I just installed Ubuntu 12.04 (which is great, as usual :D), but I'm searching the screensaver utilities in Unity (until then I used gnome-panel) and I can't find it. I did some quick research on the web and read that Ubuntu 12.04 is shipped with no screensaver. I would like to know if it is true, and if it is, where can I find and install them, other than xscreensavers, which are a little outdated to me.

Have a nice day !

---

### Post by Frogs Hair on 2012-06-23
I don't know of any other than X Screen Saver. I agree that the default screen savers for X are very outdated. Though I don't need a screen saver I did install it in 11.10 to see what it was like.

---

### Post by zombifier25 on 2012-06-23
I wouldn't call a software last updated September last year outdated. Besides, you don't have a choice anyway; xscreensaver is the ONLY screensaver pack and manager available for GNOME/Unity.
Fell free to install it
```
sudo apt-get install xscreensaver xscreensaver-data xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra xscreensaver-screensaver-bsod xscreensaver-screensaver-webcollage
```
Remove any packages you don't want from the above list. Then add xscreensaver -no-splash to startup.

Also remove gnome-screensaver (which does nothing more than blanking the screen) to avoid conflicts:
```
sudo apt-get remove gnome-screensaver
```

If you want Ctrl + Alt + L to lock the screen, run this command:
```
sudo ln -f /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```

---

### Post by le_phoceen on 2012-06-23
Hi,

I just installed the xscreensaver family of screensavers and it works. 

Thanks !

---

