---
title: "FVWM titlebar help?"
date: 2009-08-28
forum: Desktop Environments
---

### Post by TheKid965 on 2009-08-28
I'm not sure on which subforum this question belongs, but Desktop Environments seems close enough for my purposes.

I've recently rediscovered the simple joys of tweaking an FVWM configuration.  I haven't played much with FVWM since the late '90s, or around the time when GNOME and/or KDE became Good Enough for daily use, and honestly I'd quite forgotten how zippy it could be on my computer.

My question relates to one specific effect in FVWM that I'm going quite crazy trying to achieve, but cannot figure out the proper way to go about getting it.

I want to put horizontal stripes in the titlebar area, similar to the ones seen in the old MacOS before it became Aqua-fied.  I don't mean I want to use pixmaps or change the basic Motif-ish look and feel of FVWM's windows -- I actually kinda like the Motif look, it's simple and clean without being cheap-looking, and it stays out of my face enough for me to concentrate on my work -- I just want to add the barred effect to the MWM style.  I know this can be done, because I've seen it in various FVWM screenshots over the years, such as [this one](http://www.fvwm.org/screenshots/desktops/Thomas_Adam-desk-1280x960/screenshot.png) from the official FVWM site (the effect I want can be seen in the rolled-up "Shannon" window).  I assume this is done by issuing a TitleStyle command somewhere in .fvwm2rc, and/or use of vectors, but I'm still a relative newbie with taming this beast and would like a nudge or two in the right direction.  (And yes, I've tried looking in the provided .fvwm2rc for the screenshot in question, but couldn't find anything helpful for what I wanted.)

Can anyone help me out with this?  I'll be willing to post any configuration file from my ~/.fvwm directory on demand, if necessary.

---

### Post by jpkotta on 2009-08-29
```
Style * StippledTitle
```

---

### Post by TheKid965 on 2009-08-29
Awesome, that did it!  Thanks.  

(Something as simple as that, you'd think I could find it easier in the docs...)

---

