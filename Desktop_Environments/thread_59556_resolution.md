---
title: "resolution"
date: 2005-08-24
forum: Desktop Environments
---

### Post by Xalow1 on 2005-08-24
Hey all

I was wondering what command or setting somewhere, if there is one, to change my max resolution.  Once before in a previous install, the installer asked me to check the resolutions I wanted the computer to use, and then it would try the highest, being 1600x1200, and use that.  This install however, It never asked me for that option, and the highest im able to get out of it is 1280x1024, and I have a 1600x1200 monitor.  Help would be greatly appreciated, thank you.

-Brendan

---

### Post by humanity_to_others on 2005-08-24
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Xalow1 on 2005-08-24
wow thank you very much that helped find where the options are, but when i even tell it throughout the setup that i only want to use 1600x1200 @ 60 then the configuration finishes and nothing changes, and under screen resolution in preferences there are no new options

---

### Post by kamiccolo on 2005-08-24
Reboot your system. I had the same problem and it got resolved with this command.
After rebooting, 1600*1200 is available.

---

