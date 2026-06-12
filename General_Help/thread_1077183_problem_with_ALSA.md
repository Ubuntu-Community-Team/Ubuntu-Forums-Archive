---
title: "problem with ALSA"
date: 2009-02-22
forum: General Help
---

### Post by Coolvortex on 2009-02-22
Hello everybody, I need a little help if you have time. I know that issues with alsa + multiple audio cards are common and everything, but I tried every guide and document and didn't find anything or maybe I just couldn't. Anyway, this is the problem. I have a motherboard with a realtek ac97(nvidia CK804). Then, since I'm a guitarist and need to record some stuff sometimes, I have this Terratec Phase 22 card, which I'm only interested in using under windows though. It's not a normal sound card but it's only made for recording and that kind of things. For some strange reason though, alsa seems to like more the Terratec than the realtek, and always puts that one on default. So everytime I reboot, even if I chose to use the realtek from system-preferences-audio, I can't hear no sound, and the volume applet goes back to the terratec. If I open the shell and use sudo alsa force-reload, then everything works fine.
I would also like to say that if I chose to use the OSS drivers from system-preferences-audio everything works fine even after rebooting, but there are some problems, for example, with flash videos, and other stuff.
I had some ideas on how to solve this problem, for example telling alsa to always use the realtek, or to never use the terratek, or just removing the module that supports the terratec card (I think it should be snd_ice1724 but I'm not sure), but I don't know if these things can be done nor how to do them.
I thank you in advance for the help

---

### Post by Coolvortex on 2009-02-23
can anybody help? sorry for bumping but...

---

### Post by TenPlus1 on 2009-02-23
Go into the Multimedia System Selector in Prefs and under ALSA, select the device you want to use as default...

Note: if you cant see Multimedia System Selector in your menu, right-click on the menu and goto Edit Menus, then search for it there, tick the box and press OK... Not it'll be available...

---

