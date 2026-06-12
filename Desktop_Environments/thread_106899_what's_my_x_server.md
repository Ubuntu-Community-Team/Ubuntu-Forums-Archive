---
title: "what's my x server?"
date: 2005-12-21
forum: Desktop Environments
---

### Post by harisund on 2005-12-21
I am trying to understand the difference between Xorg and Xfree86. Could some one point me somewhere? 

The reason is, when I tried Knoppix earlier, I found a XFree86-4.conf file and in Ubuntu I don't? Also I read that the latest version of Xorg, version 7 is released. So what does Ubuntu use? 

Thanks.. just trying to understand the basics here.. 

!

---

### Post by cwaldbieser on 2005-12-21
[QUOTE=harisund]I am trying to understand the difference between Xorg and Xfree86. Could some one point me somewhere? 

The reason is, when I tried Knoppix earlier, I found a XFree86-4.conf file and in Ubuntu I don't? Also I read that the latest version of Xorg, version 7 is released. So what does Ubuntu use? 

Thanks.. just trying to understand the basics here.. 

![/QUOTE]
The detailed history is here:
[http://en.wikipedia.org/wiki/X_Windows]("http://en.wikipedia.org/wiki/X_Windows")
The short version is that XFree86 was a project for the X Display server.  The project maintainers gave a lot of folks in the community a bad vibe, and folks were unhappy with the project management.  Xorg was started as a fork of the XFree86 project.  The XFree86 project changed their licensing terms at some point which made waves with a lot of the major distros, and eventually the distros replaced XFree86 with Xorg.  Xorg is now the dominant project, while XFree86 has become more obscure.

---

