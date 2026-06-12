---
title: "Uninstall Quake4/UT2004 Demos"
date: 2006-03-04
forum: Gaming &amp; Leisure
---

### Post by opticyclic on 2006-03-04
I downloaded the Quake4 and UT2004 Demos and installed them using > sudo sh quake4-linux-1.0-demo.x86.runand after a lot of fiddling managed to get Quake4 working (but not UT2004, stuck with just a splash screen).
However, the FPS was rubbish and the sound was like it was coming from Stephen Hawkings voicebox! :mrgreen: 

I have come to the conclusion that my system is a bit crap for the latest games so I decided to remove the demos.
My problem is that I am not sure what to do.
The /home/username/.quake4-demo directory is only 14MB in size yet the .run file is 327 MB.

Where are all the other files kept?

How do I remove games/apps installed with sudo sh name.run?

---

### Post by polpak on 2006-03-05
that depends on where you chose to install them to. Most likely they're in /usr/local/games or some such. You just have to find the appropriate directory ( possibly by rerunning the installer and see what the default is) then remove the files from there.

---

