---
title: "Conky and other windows"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by cimnik on 2007-12-11
I found and modified a conky script on the internet. I'm really happy with it.

I use conky to replace gnomes top panel, but I can either get conky to sit only above or below other windows. I want it to always be visible, so is there any way to change the desktop surface area so that if I maximize a window it doesn't cover conky?

thanks in advance.

---

### Post by tombean on 2007-12-12
I got the same issue...
I'm looking for a solution, too.

---

### Post by notwen on 2007-12-12
Don't think this would be possible, being conky resides on your desktop or either 'always-on-top'.  If you specify in your conky config for conky to be a normal window, maximizing another window would simply maximize said window over conky.  You may want to ask in #conky on freenode if they have any recommendations.  Good luck w/ this. =]

---

### Post by mozetti on 2007-12-12
If you run compiz, you can specify certain windows to remain on top using the Compiz Config Settings Manager. Find that option and use:```
name=conky
``` assuming the program name is conky. For example, I have my awn set to be always on top with Compiz and the code I use in the option for always on top is:```
name=avant-window-navigator
```

---

