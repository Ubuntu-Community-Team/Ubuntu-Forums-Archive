---
title: "A few problems with Lubuntu Yakkety and Baytrail tablet"
date: 2016-10-26
forum: Desktop Environments
---

### Post by kiina on 2016-10-26
A few problems I've found when using this new Lubuntu.

**1. problem**
Onboard keyboard is too small on login screen, how to fix it?
[[IMG]https://s17.postimg.org/qywvbwoqz/onboard_login.jpg[/IMG]]("https://postimg.org/image/qywvbwoqz/")

**2. problem**
How to use right click on touchscreen? Do I need to install something for gestures? Chrome-browser is only where gestures works.

**3. problem**
Touchscreen does not work near left & right border. Can't press close -button when window is maximized. Screen calibration does not help.

**4. problem**
Tablet has HiDPI -screen. How enable HiDPI?

[B]5. problem
[/B]Easyway to change screen brightness, is there any?(no keyboard, only onboard)

[B]6. problem
[/B]Soundcard is dummy output, how to fix. 
```
sudo alsa force-reload
``` does not help

```
aplay -l
``` found 3 devices.
Intel HDMI and two bytcr-rt5640 soundcards.

---

### Post by kiina on 2016-10-26
ok, I got some tips to fix these problems.. For HiDPi I should install other DE, and that audio problem is fixed [16.04-linuxium]("http://linuxiumcomau.blogspot.com/2016/10/running-ubuntu-on-intel-bay-trail-and.html").. I close this thread and make clean fresh install.

---

