---
title: "Screensaver makes Compiz skydome go black"
date: 2009-01-11
forum: General Help
---

### Post by patmalcolm91 on 2009-01-11
After upgrading to Intrepid, I've encountered a problem. After the screensaver (the regular one, not the compiz plugin) comes on and I move the mouse to turn it off, the Compiz skydome is black, rather than the image I have set for it.

Doing "killall compiz && compiz &" restores the skydome to the original state, but only until the screensaver comes on again.

I've endlessly searched on this, and I've tried several different things, but I'm completely puzzled as to what the problem is. Any help is greatly appreciated.

Patrick

EDIT: i forgot to mention, my graphics card is the intel 915GM

---

### Post by patmalcolm91 on 2009-01-16
anyone?

---

### Post by mssever on 2009-01-16
I have the same problem, with the addition that some other Compiz features also die (which are actually more annoying than losing my skydome image). I've resorted to using fusion-icon so that I have an easy way to restart Compiz. But that's a workaround, not a fix.

My machine is a Lenovo ThinkPad R61i with an Intel Mobile GM965/GL960 video card.

---

### Post by patmalcolm91 on 2009-01-25
Is anyone else having this problem? Does anyone have an idea of how to fix it or find the cause?

---

### Post by mssever on 2009-01-25
I wonder if switching from gnome-screensaver to xscreensaver would do the trick...

---

### Post by patmalcolm91 on 2009-01-26
The same thing happens with xscreensaver running instead of gnome-screensaver. I think this might be a compiz problem, If i get some time, I'm going to try to reinstall the relevant plugin via apt and from source. I'll report back when I do...

---

