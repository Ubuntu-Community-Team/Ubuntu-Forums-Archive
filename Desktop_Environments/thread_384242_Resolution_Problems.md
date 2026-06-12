---
title: "Resolution Problems"
date: 2007-03-14
forum: Desktop Environments
---

### Post by Franco84 on 2007-03-14
I've been making some serious progress lately. I finally found the best way to install the ATI drivers on my system. Direct rendering is a go. But now..

My monitor has a native resolution of 1440x900 (widescreen monitor) which I had to adjust after logging in. However, the log in screen is stuck to 1920x1200 or 1920x1200. Either way, I can't click the options button because it extennds past the monitor. I want to change my sessions to XGL. 

Anybody know a way to fix this? Thanks in advance!

---

### Post by taurus on 2007-03-14
You need to modify your /etc/X11/xorg.conf.  Boot into recovery mode from GRUB menu and at the prompt, run

```
nano -Bw /etc/X11/xorg.conf
```
Now, remove the resolutions you don't want to use and add the one you want to use at the beginning.  Save it and exit with <Ctrl>o and <Ctrl>x. 

Reboot with

```
shutdown -r now
```

---

### Post by Franco84 on 2007-03-14
Thank you! I can't wait to go home and test it out.

---

