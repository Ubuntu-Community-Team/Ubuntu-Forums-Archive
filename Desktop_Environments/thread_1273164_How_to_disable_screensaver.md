---
title: "How to disable screensaver"
date: 2009-09-23
forum: Desktop Environments
---

### Post by el_kolo on 2009-09-23
HI,

I removed screensaver (apt-get remove screensaver) from my system but it still works. I want to completelly disable this function. Also, I configured properly power mangment but it doesn't help. How can do this? Maybe this black screen is not a screensaver. Maybe ubuntu turns off monitor after a while? Everything in configuration seem to be ok. 
Please help.

---

### Post by bruno9779 on 2009-09-23
The blank screen is the default screensaver.
You can switch it off in Preferences>appearance
On the screensaver tab you have options for the behavior of the screen when idle.

one is a bar that lets you decide idle time, and a tick box to enable screensaver when idle

---

### Post by el_kolo on 2009-09-23
In don't have screensaver tab in Apperance;/

---

### Post by bruno9779 on 2009-09-23
You are right.
How about a screensaver entry in Preferences?

I am writing from a M$ computer and am going only by memory, but if you don't have a screensaver entry in preferences, than you may have to reinstall screensaver package

---

### Post by etnlIcarus on 2009-09-23
```
sudo aptitude remove gnome-screensaver xscreensaver xscreensaver-data
```

If these aren't installed, you shouldn't get any screensavers popping up.


That said, power management is a different issue. If you uninstall or disable any of the power management tools, the xserver will automatically put itself to, "sleep", after around 20 minutes. You need to have gnome-power-manager installed, running in the background and properly configured to prevent your monitor from going to sleep.

*That said*, letting it go to sleep after a certain period of inactivity is a sensible thing to do.

---

### Post by el_kolo on 2009-09-23
> **etnlIcarus said:**
> ```
sudo aptitude remove gnome-screensaver xscreensaver xscreensaver-data
```If these aren't installed, you shouldn't get any screensavers popping up.
  

I removed this packages. I have also gnome-power-manager and it didn't work properly.

I have found resolution here
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46575](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46575) 

Best way to fix this problem is to add ServerFlags section to xorg.conf.

Thanks for your interest!

---

