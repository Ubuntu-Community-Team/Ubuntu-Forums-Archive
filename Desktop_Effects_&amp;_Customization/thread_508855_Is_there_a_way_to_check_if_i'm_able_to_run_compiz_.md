---
title: "Is there a way to check if i'm able to run compiz fusion??"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by graymaster on 2007-07-24
Is there a way to check whether or not my computer is able to run compiz fusion?? I can tell you my systems stats if i need to. Thanks alot, Graymaster

---

### Post by benx009 on 2007-07-24
i'm pretty sure that if you can run compiz, you can run compiz fusion.  the following are the most important: 

1) your video card chipset
2) your cpu chipset & speed 
3) the amount of RAM you have in your system

if you have decent specs across the board, you can probably run compiz fusion

---

### Post by Happy_Man on 2007-07-24
Yeah. Put ```
glxinfo | grep direct
``` into the terminal, and if it comes up as no... then you won't be able to run it without better drivers.

---

