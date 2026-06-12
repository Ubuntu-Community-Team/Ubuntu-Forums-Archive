---
title: "Eee PC Desktop Effects Problem"
date: 2009-03-14
forum: Desktop Environments
---

### Post by Herriott101 on 2009-03-14
I have had a problem with the desktop effects while using Ubuntu 8.10 with my eee pc 901.

The eee pc has worked fine for quite a while, it had some simple desktop effects (nothing too fancy or resource intensive) and hasn't caused any problems.

However, after trying to get it to work with a projector I gave up and returned to working normally, only to find that the visual effects no longer worked.

I tried to enable them again only to get the message "Desktop effects could not be enabled." (it usually tries to check for available drivers first, I'm not sure if this is part of the problem).

I would normally not be to bothered by this, however switching windows using alt tab has become annoying as I no longer see the windows in the box before I change to it. Also, when changing workspaces I no longer get the nice black box appear as I change spaces and the change is no longer as smooth. I know these issues aren't that big but they would be nice to get back.

Thanks in advance for any help,

Alex

---

### Post by mgfletcher on 2009-04-06
Hi Alex

The exact same thing has just happened to me... I used grandr to set up the projected screen.  I turned compiz off and now it will not turn back on again.

Any solution present itself?
[I]
Edit - I think I solved it, you need to edit the xorg.cof file manually. open the file and edit the screen section so that the line starting with virtual reads - Virtual 1024 600

then save, restart X and my desktop effects then could be enabled :-) [/I]

---

