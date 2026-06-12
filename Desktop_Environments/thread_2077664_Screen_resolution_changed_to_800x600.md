---
title: "Screen resolution changed to 800x600"
date: 2012-10-29
forum: Desktop Environments
---

### Post by xmeltrut on 2012-10-29
I turned my computer on this morning to discover that my screen resolution had changed. It normally runs at something reasonably high (1400-1600, or sometime like that), but it had now been reduced to 800x600 and didn't fill my monitor, leaving a large black border round the entire screen.

That is the only option I now have in System Settings > Displays.

I've tried running apt-get upgrade and update, and unity --reset.

I'm running the "NVIDIA accelerated graphics driver (current version)", which is the same one I've always been running. I tried switching to the post-release updates version, but that stopped X/Gnome from loading at all, and I had to switch back to the current release from the command line.

When I run xrandr, I get:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
800x600 75.0*

Any ideas? Thanks.

---

### Post by xmeltrut on 2012-10-29
I've resolved the issue. Here is what I did:

* Exit X (sudo service lightdm stop)
* Remove all Nvidia drivers - sudo apt-get purge nvidia*
* Reboot the system
* Open up System Settings > Additional Drivers
* Select the first "NVIDIA binary Xorg driver, kernal module and VPDAU library"
* Click activate
* Reboot the system again

---

