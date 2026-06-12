---
title: "X problems--refresh rate and size"
date: 2005-12-23
forum: Desktop Environments
---

### Post by duminas on 2005-12-23
I've issued
```
sudo ddcprobe|grep monitorrange
```To fetch the horizontal sync and vertical refresh values for this monitor, which are **30-86** and **50-160** apparently. Then I did a
```
LANG=en_GB.UTF-8 sudo dpkg-reconfigure xserver-xorg
```(Switches it back to English, since my system language is Japanese and the base terminal doesn't like that.)

I enabled 1600x1200, 1280x1024, 1280x960, 1024x768, 800x600, and 640x480. Went Advanced and entered the rates I got from the first command, and the configuration finished successfully.

The problems I am running into are as follows:
1600x1200 leaves a weird vertical bar on the right side of the screen (with a white glare at the right) at 65 Hz. 1280x1024 works decently (75 Hz) aside from the screen bouncing slightly--gives me a headache if I look at it too long. Degaussing helps, but it comes back in short order. Anything lower looks pretty bad on this size screen (19 inch) due to how blown up it gets.

Any ideas? At present, I do _NOT_ have a manual for this monitor.
Thanks.

---

