---
title: "Force 800x600 resolution on ubuntu 11.04"
date: 2011-07-15
forum: Desktop Environments
---

### Post by paulfurtado91 on 2011-07-15
Hi All,

I hate needing to set custom resolutions in linux. Ubuntu 11.04 isn't making it any easier.

So, I have 7" touch screen that attaches via HDMI. I'm using the Pandaboard so I'm not sure what graphics card driver I'm using. Xrandr cannot figure out my screen's proper resolution and I can't find the xorg.conf file.

What should my next step be? If there's some generic option that says force 800x600 on all screens on all graphics cards, that would probably be the easiest way to do this.

I'm usually not the type who likes to jump and ask things in the forums, but I've already spent a ton of time on this and I need to get this answered asap for my project to continue.

Really, thanks for any replies,
Paul

---

### Post by wildmanne39 on 2011-07-15
> **paulfurtado91 said:**
> Hi All,

I hate needing to set custom resolutions in linux. Ubuntu 11.04 isn't making it any easier.

So, I have 7" touch screen that attaches via HDMI. I'm using the Pandaboard so I'm not sure what graphics card driver I'm using. Xrandr cannot figure out my screen's proper resolution and I can't find the xorg.conf file.

What should my next step be? If there's some generic option that says force 800x600 on all screens on all graphics cards, that would probably be the easiest way to do this.

I'm usually not the type who likes to jump and ask things in the forums, but I've already spent a ton of time on this and I need to get this answered asap for my project to continue.

Really, thanks for any replies,
Paul
Hi, you actually have to create the file in natty. Here is a link that is easy to follow for setting resolution in xorg.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

To create the file type this in a terminal
```
gksudo gedit /etc/X11/xorg.conf

```
Then when you are done save it and restart your system.

---

