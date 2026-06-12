---
title: "Logging/rebooting etc gives me a blank screen."
date: 2006-09-05
forum: Desktop Environments
---

### Post by SvanteH on 2006-09-05
I get a black screen when logging out/shutting down/rebooting/changing user/session.

Most strangly is that I can press alt-f1 to 6 entering me to some "ttyX" where X is the F-key I am on, I entered to a command line and I could hear my music etc so I wasn't really logged out, but I couldn't get back into the desktop enviroment, anyone know what I am speaking about?

---

### Post by artinla on 2006-09-05
I don't know for sure, but you are probably running NVidia or ATI drivers.  I had the same problem and removing "Splash" from the grub runline made the problem go away.  You don't get the nice graphical startup, but the black screen upon logging off or shutting down goes away.

Just hit esc when the system is booting up, highlight the line that you want to change and hit "e" to edit the runline.  Get rid of the word "splash" at the end.

Art

---

