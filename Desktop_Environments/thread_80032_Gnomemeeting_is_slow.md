---
title: "Gnomemeeting is slow"
date: 2005-10-21
forum: Desktop Environments
---

### Post by avc on 2005-10-21
Gnomemeeting used to be faster in Hoary. Now it's eating up over 90% of my cpu and got my laptop fan whirring like crazy! It takes almost 5 seconds just to load a blank new tab on firefox. I'm on a Pentium 3 600 MHz, and although I know it's slow by modern standards, I'm running gnomemeeting with my friend who has got a 400 MHz Celeron, and that computer is doing fine. Moreover, like I said, it was running fine under Hoary. What gives?

If there are no apparent solutions, can I at least regress to a previous version somehow? I've got 1.2.2 installed.

OSS is such a great idea, but I've been losing way too much sleep trying to get it to work... :(

---

### Post by avc on 2005-10-23
:mad: I got so frustrated I installed ion2 to replace the Gnome desktop environment. Surprisingly, it worked... somewhat. Most of the time now, gnomemeeting is using less than 40% of my cpu. Great! But then once in while, it craps out again and starts eating 98%.

side note: ion is so much faster than any other X display manager I've used (besides ratpoison). I didn't completely figure out my gnomemeeting problem, but at least I discovered a cool gnome alternative. ([screenshot]("http://studiogangster.com/pics/05/ion_nerd.jpg"))

---

### Post by avc on 2005-10-24
I think I figured it out, in case anyone else ever has this problem. My computer starts acting up when the USB webcam (a Logitech QuickCam Pro 4000) is **unplugged**. It seems that gnomemeeting is constantly querying for it and eating up CPU cycles doing so. **Workaround:** go to preferences and click "Detect Devices" in the Video Devices section. It should result in gnomemeeting realizing there are no devices connected and stop it from querying.

---

