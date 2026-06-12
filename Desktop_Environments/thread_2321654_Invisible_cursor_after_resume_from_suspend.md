---
title: "Invisible cursor after resume from suspend"
date: 2016-04-23
forum: Desktop Environments
---

### Post by nick251 on 2016-04-23
Hello,

I have an Aspire One D250 (Intel Atom-based netbook) on which I've installed Lubuntu 16.04.  Upon resume from suspend, the cursor is visible until I click the unlock button and then disappears as soon as I'm back to my desktop.  Alt+F1 followed by Alt+F7 to toggle out of the graphical environment and back makes it reappear.  Does anyone have any idea what could be wrong?  I tried using gdm instead of lightdm, but the former hangs on resume from suspend.

I also tried the following with no luck
```
 gsettings set org.gnome.settings-daemon.plugins.cursor active false
```

Thanks

---

### Post by nick251 on 2016-04-23
Upon further investigation, this is actually a known bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640)

Affects xubuntu too:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604)

I guess that's that until a fix is released.

---

### Post by Mrinmoy_Dey on 2016-04-25
Yes. It's a known bug and I am also affected. As a temporary solution I disabled auto screen locking. But Ctrl + F7 is bringing it back (Alt +F1 followed by Alt + F7 did nothing for me!). So thanks for the intermediate solution.

---

