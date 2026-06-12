---
title: "Mouse package name?"
date: 2009-01-26
forum: General Help
---

### Post by Arenlor on 2009-01-26
I'm wondering what the mouse package's name is, I am using a laptop with a touchpad and the mouse is going somewhat insane. I'm on Jaunty. I just want to report a bug on it. It's the full mouse, both clicking and moving is screwed up.

---

### Post by lensman3 on 2009-01-26
From a command line do: "ps ax | grep gpm"

The TEXT mouse  program is called gpm and the grep will show which mouse the system thinks it is using.  See if it is correct.

For X11 the mouse is built into the X11 programs and drivers now (I think). So if your mouse isn't working you will have to probably contact the X11 development group and give them your graphics card/chip details.


Hope this helps.

---

