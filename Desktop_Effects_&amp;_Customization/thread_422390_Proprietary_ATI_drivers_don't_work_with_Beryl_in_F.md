---
title: "Proprietary ATI drivers don't work with Beryl in Feisty"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Sethramoth on 2007-04-25
I don't know if this has already been discovered, but I have found that (at least on my system) the optional proprietary drivers for ATI video cards don't work with Compiz or Beryl in Feisty. When I try to enable Compiz using the proprietary drivers a message comes up saying "The Composite extension is not available". Compiz and Beryl both run perfectly fine with the default open-source drivers, so I'm not worried, I just thought it might be worth noting. I'm using a Radeon 9600XT 128MB.

---

### Post by quinntar on 2007-04-25
Hi mate, I'm actually using a X200m ATI  with my Feisty. The thing is that you've to use an XGL session to use ATI proprietary drivers for some ATI video Cards that cannot use AIGLX driver ina gnome session. As a consequence it seems that your card does not support 3D on normal session, try to install an XGL session and login with tht session. Normally, Beryl should work. I succeed with an ATI 9000 to use AIGLX though, you can find the list of supported card on Ubuntu wiki I think.

Hope you'll succeed.

PS: anyway all worked perfectly for me on Edgy, and now I'm metting some problems with feisty, Waiting for an upgrade maybe

---

### Post by infinitelink on 2007-05-01
Thanks, but, does anyone have any REAL fixes to this? I read elsewhere that for some reason the propriety drivers require compiz to be set on false in some files, but...that's still not helping anyone or trying to figure-out the why, or "what happened" and fix it...  ?  The only reason I go further (than post 2) is that I read a thread where one guy had an ATI 200m that didn't work, another had the same that did...so there might be some work-around somewhere. If not, oh well. 

I'm running an ATI 9700 by the way, so me and the guy started this could both benefit, most likely, from the same fix (if any).   : )

---

### Post by lbyrd33 on 2007-05-01
Right now using xgl is the only fix to this problem. See this thread for how to set up: [http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643). As of now, only if you use the mesa drivers are working with composite and beryl. However, setting up xgl seems to work ok with the propreitary drivers.

---

