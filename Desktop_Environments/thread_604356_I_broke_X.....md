---
title: "I broke X...."
date: 2007-11-06
forum: Desktop Environments
---

### Post by DraK on 2007-11-06
Ok, I had a lovely looking GUI on 7.10 with Compiz and the restricted Nvidia drivers. I installed the proprietry NVIDIA drivers and now X loads, I login, it starts loading and then i just get a white screen with the mouse pointer...

I was trying to install NVIDIA driver so i could get my screen resolution back to 1600x1050.  Restricted driver did not give me this option.

How can I attempt to fix it now? Still learning more of the "ins" of Linux

---

### Post by ohzopants on 2007-11-07
The good news is that you still have a fully functioning system.  When it is at the white screen, you can simply press ctrl+alt+f1 (or f2, or f3, or f4... al the way to f6) to get a command line.

You should check your /etc/X11/xorg.conf file and tell us what is listed in the "Screen" section.  In the same folder as xorg.conf, the nvidia installer should have made a backup copy (typically with the same name, but with a timestamp appended to it).

Did you disable and uninstall the restricted driver first?  If you just installed over them, that is probably where the problem came form.

Pre-Gutsy I used to have the "official" drivers also, but they tended to be a royal pain in the *** since they broke everytime there was a kernel update.

---

