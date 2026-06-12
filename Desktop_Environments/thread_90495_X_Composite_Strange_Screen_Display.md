---
title: "X Composite: Strange Screen Display"
date: 2005-11-15
forum: Desktop Environments
---

### Post by fate on 2005-11-15
My apologies first in the case this is posted somewhere else. I have no idea what the technical term is for the problem I'm experiencing. :)

I'm running:

AMD64 3ghz w/ Gigabyte K8NS
1gb RAM
BFG Nvidia 6600GT OC (2 DVI-out card)
(2) Samsung 193p LCDs (twinview enabled, xinerama disabled)
Ubuntu 5.10 i386. (would use 64 ed., but I can't run some packages with it's kernel)

I'm relatively new to linux. I've used it on and off throughout the years, but I haven't really sat down and tried figuring it out. Recently the bug hit me to do just that, and.. well.. I think I'm making some considerable progress.

However, after wanting some eyecandy for the desktop and trying Composite on for size, I noticed what appeared to be a pretty scary thing pop up on both of my monitors. Once Gnome loads with xcompmgr or Xfce loads with it's own composite engine, both of the monitors briefly flicker and come back with what appears to be a badly drawn screen. That sounds to me like a terrible way to explain it, but that's about all I can give. It looks as if the LCD refresh was screwed for a split second or something. The kicker, to me -- I can move a terminal window or whatever open window over this badly displayed portion of the desktop and it'll come back just fine as if nothing ever happened.

I've read Twinview and Composite have some issues -- would this be related?

Twinview works great and I know Composite is working because I see the visible transparency and window shadows. They both work well after this glitch is cleared up by "wiping" over whatever is badly displayed with another window.

Whether the post is answered or not, I feel I need to say thanks to those who've helped in making Ubuntu and it's community possible. Ubuntu, despite the issues I'm having with Composite, seems to be a very solid distro. Please keep up the good work. :)

---

### Post by fate on 2005-11-16
And whether or not it's a symptom of the problem, I'm unsure, but when moving a window around on the desktop gkrellm tells me the CPU usage is 99%.

I've used Synaptic to install the nvidia driver, allowglxwithcomposite is enabled and renderaccel is enabled.

Any suggestions on a place of where I might be able to start to diagnose my above post and this?

---

