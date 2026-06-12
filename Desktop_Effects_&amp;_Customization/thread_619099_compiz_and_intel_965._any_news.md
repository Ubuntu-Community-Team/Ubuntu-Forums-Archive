---
title: "compiz and intel 965. any news?"
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by arod0405 on 2007-11-21
I'm not so happy with intel graphics:
on my desktop intel 965 integrated graphics doesn't work with compiz. afaik driver is blacklisted because of xv video issues when compiz is enabled.
this is so frustrating because it did work with feisty (vith video issues maybe) and because I thought intel graphics would play well with linux.
on my laptop intel 955gm graphics works well. but then again tv-out crashes or outputs black and white video.
I read a new intel driver (2.2) has just been released. Does anyone know if this solve any problem?
Thanks

---

### Post by dentaku65 on 2007-11-21
Save your xorg.conf 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

And try to change in xorg.conf your:

```
        Driver          "intel"
```
in
```
        Driver          "i810"
        VideoRam 65536

```

Reboot and (better) log to X with anoher user (changing the video driver I've experienced a loss of configuration, eg firefox settings, with my own user)

---

### Post by arod0405 on 2007-11-22
afaik i810 is deprecated and intel driver is the one currently developed. I'm hoping someone fixes these bugs instead of using some old driver.
anyway I'll try. Thanks

---

### Post by oliver123 on 2007-12-05
It seems that the 965 adapter is only blacklisted because XV (X Video acceleration) doesn't work with compiz. However, you can disable XV in most media players and use non-accelerated video output - I suppose it's fast enough, and when an updated driver is released, you can switch back to XV.

For totem and other gstreamer-based video players, you can change this by running "gstreamer-properties" and on the Video tab, under Video Output select "X Window System (No XV)". Totem should now play videos without crashing.

---

### Post by Fabiotc on 2007-12-17
Verify if xgl is instaled:
sudo apt-get install xserver-xgl
Follow this tutorial:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Install the packages: "compizconfig-settings-manager" and "fusion-icon"

To install "fusion-icon", add in your sources.lst:
deb [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse
deb-src [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse



Regards from Brasil :)

---

### Post by topolino on 2007-12-30
Hi,

I understand that the Intel 965 graphics chipset is blacklisted by Compiz because XV doesn't work with Compiz running. However, does the problem come from:
- Compiz
- Intel 965 driver
- Something else

From where should a fix come from?

Thanks!

---

### Post by Forlong on 2007-12-30
It's a driver and AIGLX problem.
But you can skip the blacklist if you like with ```
SKIP_CHECKS=yes compiz
```

---

### Post by sceo on 2008-01-20
Is there a post or developer blog or something I can follow so I can stay on top of when they get this fixed?

---

### Post by Dynaflow on 2008-01-21
> **sceo said:**
> Is there a post or developer blog or something I can follow so I can stay on top of when they get this fixed?

This would be the place:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/148247]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/148247")

---

### Post by Dynaflow on 2008-01-29
Looks like it's not happening for Hardy:  [http://www.realistanew.com/2008/01/12/compiz-updates/]("http://www.realistanew.com/2008/01/12/compiz-updates/")

See you in October, Spinning Cube.

---

### Post by rmcnaught on 2008-02-08
SKIP_CHECKS=yes compiz

can someone tell me where this option is set?  ie which file?

Thanks

Robert

---

