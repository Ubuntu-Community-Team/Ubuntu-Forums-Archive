---
title: "Issue with restricted drivers and a KVM switch"
date: 2008-09-19
forum: Desktop Environments
---

### Post by Wintaru on 2008-09-19
Greetings everyone.

I've installed Hardy on a PC I have with an ATI Radeon 9600 All-in-wonder pro connected to a Westinghouse 17" monitor via an IOGear KVM switch.  The install went perfectly and all looked good until I enabled the "ATI accelerated graphics driver".  Once I rebooted, my monitor displayed an Out of Range message and nothing could be seen.  I had backed up my xorg.conf file and so I restored that and I have a desktop I can see again, but all of the graphics are rendered very slowly now.

I'm not sure how to proceed from here unfortunately and was hoping someone could point me in the right direction.  Thanks!

Edit:

To further specify what I want, first I would like to get the graphics working the way they did before I enabled the restricted driver and then second, I would like to get the restricted driver working so I can enable compiz.

---

### Post by Wintaru on 2008-09-19
Well I figured out the first problem, changing the visual effects section of Appearance to None stopped the rendering issue but now AWN doesn't work either, I'm assuming because it needed that enabled.

---

