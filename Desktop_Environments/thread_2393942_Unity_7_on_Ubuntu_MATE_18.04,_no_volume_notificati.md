---
title: "Unity 7 on Ubuntu MATE 18.04, no volume notification"
date: 2018-06-10
forum: Desktop Environments
---

### Post by chrisshyi on 2018-06-10
Hey everyone,

Installed Unity 7 on Ubuntu 18.04 MATE and everything's worked well so far. The only exception is I don't get a notification in the upper right corner anymore whenever I change the volume using the keys on my keyboard, wondering if someone could give me some tips on setting that up. Thanks!

---

### Post by cruzer001 on 2018-06-10
How did you install Unity7?

I ask because I wish to try this.

---

### Post by mc4man on 2018-06-10
install notify-osd package

---

### Post by monkeybrain20122 on 2018-06-11
> **cruzer001 said:**
> How did you install Unity7?

I ask because I wish to try this.

```
sudo apt install ubuntu-unity-desktop
```

When prompted choose lightdm as default

If need touchpad

```
sudo apt install xserver-xorg-input-synaptics
```

Reboot, that's it.

The meta-package ubuntu-unity-desktop pulls in stuffs that you may not need like gnome-mpv and youtube-dl. You can uninstall those. If don't need gnome shell (assumming you are on default 18.04) you can uninstall it.

---

### Post by deadflowr on 2018-06-11
Is it only the sound notifying that doesn't work?
Or is it all notifying?

If only sound, then try this 
remove the pulse folder from your user's home folder at
/home/user/.config/pulse
then log out and log back in.

It feels like one issue wouldn't be connected to other, but for some reason this method has worked for me in the past.

The pulse folder will get regenerated anew on login.
So the most you might have to do is reset any non-default sound settings again in System Settings > Sound. 

(If you do not want to outright delete the pulse folder then just move it somewhere out of the way)

((the .config folder is hidden by default,, but you can use ctrl + H in the Files program to enable showing hidden folders and files.))


Again, if this issue affects all notifying, then ignore the above, as then it's something else.

---

