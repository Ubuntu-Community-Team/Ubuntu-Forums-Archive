---
title: "Cannot copy/paste text in MATLAB - problem with X?"
date: 2009-11-13
forum: Desktop Environments
---

### Post by burningbunny on 2009-11-13
Hi-
I have a really strange issue with MATLAB:
**Most** of the time, I can't copy text to and from as well as within matlab.

I start matlab from the network like we do on all machines in the office, and on my (and only my) kubuntu machine, I cannot:

-Copy text via ctrl-C ctrl-V
-Copy text via middle mouse click
-Copy text via right-click:copy/paste


All of this neither works between windows nor in a single window, **BUT**:
If I randomly switch between windows and applications (haven't found a pattern), I can sometimes coerce matlab into copying and pasting, but only for once.
Strange effect: If I middle-click several times, I first get my copied text, then the text that I had copied before that (outside of matlab) and finally nothing.

I suspect this has something to do with X, but I have no idea where to start. Any ideas?

---

### Post by daliakopoulos on 2010-05-10
Did you ever find the solution for this? Matlab can work with both emacs and window shortcut mode. The default installation works with the emacs shortcuts (so e.g. copy would be Alt+W). In order to switch between modes go to File->Preferences and check the Keyboard attributes. Hope this helps

---

### Post by joschaef on 2011-10-05
> **daliakopoulos said:**
> Did you ever find the solution for this? Matlab can work with both emacs and window shortcut mode. The default installation works with the emacs shortcuts (so e.g. copy would be Alt+W). In order to switch between modes go to File->Preferences and check the Keyboard attributes. Hope this helps

Thank you very much, this works!

---

