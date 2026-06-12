---
title: "Ubuntu 20.04 Desktop turns off automatically when left on log in screen."
date: 2021-12-15
forum: Desktop Environments
---

### Post by mathtick on 2021-12-15
I am trying to debug this, this did not use to happen in the past. I do not remember doing anything recently in terms of changes but there have been lots of updates since I last tested this.

My use case is that I have autoreboot set on so that on power failure the system reboots, I did not have autologon set. So it would autoreboot, log in screen would should and then at some period after that if I did not log in the computer would turn off, suspend or whatever (I do not know how to tell the difference). 

I have been looking at

* dmesg
* last -x

But nothing obvious is there. 

I have been changing settings in dconf and in settings app to try to find anything that could be doing this but nothing is working so far. Testing is *expensive* (wait X minutes after a reboot) so this is not fun. 

I will try to work around by setting autologin to ON for now.

I will be away so this is pretty annoying is some setting bug has krept in over the last few years.

I don't think I have updated the firmward recently, so I *do not suspect* hardward is closing things down and it seems to be dependent on Ubuntu state (only for log in screen, not happening when logged in).

This is a DESKTOP.

---

