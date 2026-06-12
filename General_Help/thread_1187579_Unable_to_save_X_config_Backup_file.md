---
title: "Unable to save X config Backup file"
date: 2009-06-14
forum: General Help
---

### Post by gilch on 2009-06-14
Every time I restart my ubuntu the resolution reverts to 1280x960, so I have to go to NVIDIA X server to reset the resolution to 'auto'. I 'apply' it and it works fine, except when I try to 'Save to X Configuration File' I get the message to merge with existing file, then it says Unable to create new X config Backup file 'etc/XII/xorg.conf.backup'.
What should I do?
Gilles

---

### Post by merlinus on 2009-06-14
You need to use gksu to be able to save it:

```

gksu nvidia-settings

```

---

### Post by gilch on 2009-06-14
I did that and it seemed to work. I'll find out when I reboot. Thanks
Gilles

---

### Post by TheBuzzSaw on 2009-06-14
```
gksudo nvidia-settings
```
After you make your changes, click the "Save to X.org" button. It should keep your settings from then on.

---

### Post by gilch on 2009-06-15
Your recommendation did not work.
There is a box called 'Save to X Configuration file'. When I click on it it says 'Unable to create new X config backup file '/etc/XII/xorg.conf.backup''. There is button to Save to X.org as the last message said.
I am still stuck to change the settings every time I boot up.
Gilles

---

### Post by TheBuzzSaw on 2009-06-15
```
sudo nvidia-xconfig
```
Try running that before running nvidia-settings.

---

### Post by gilch on 2009-06-16
After doing what you suggest I still only get the response:

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

Gilles

---

### Post by TheBuzzSaw on 2009-06-16
OK, believe it or not, I have yet another solution. XD

While under root, rename both your original and backup xorg files to something entirely different (or move them into another folder you won't lose). Then nvidia-settings should just create a brand new xorg file. That worked for me originally (before I started using the nvidia-xconfig method).

---

