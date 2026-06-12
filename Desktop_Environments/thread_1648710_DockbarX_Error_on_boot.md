---
title: "DockbarX Error on boot"
date: 2010-12-19
forum: Desktop Environments
---

### Post by jingaling on 2010-12-19
Hi Guys,

I am having a bit of an issue with dockbarx and my desktop on boot. Everytime I boot my computer up I get the error message shown in the attached image 'screenshot'. Dockbar doesn't load on my bottom panel and my top panel seems to be in some kind of 'basic' mode.

If I click delete on the error message then re-add dockbarX applet then it works fine but as soon as I re-boot the same thing happens. Also, the 'basic' panel turns back to normal as soon as I open the appearance properties (I don't have to make any changes - just open the properties) - see screenshot01 attached.

Hope you can help guys as this has got me stumped a bit. I haven't tried un-installing and reinstalling docbarx yet.

---

### Post by Laysan_A on 2010-12-20
Well, it's been a day...have you reinstalled it yet?

I'm just guessing here (I figured you could use a bump in any case ;) ).

Try disabling zoom mode on your desktop and see if that changes the behavior. 

Maybe it has something to do with the order of initialization of your desktop effects? Reinstallation of the dockbar may place it in a different order? Perhaps disabling effects, rebooting, then re-enabling will do something with your settings to make them more compatible?

Have you checked all your logs /var/logs/ for errors? There really isn't a lot to go on here...

You might also consider installing some x debugging symbols from the repos to help with diagnosis - also for the dock, if available.

---

### Post by jingaling on 2010-12-20
Hey Laysan,

I did try to re-install but alas that didn't work either so I decided to just restore from an image I have of my desktop instead of messing around trying to troubleshoot. 30 mins later and I'm back up and running :).

Thanks for the reply though, I really appreciate it.

---

