---
title: "force maximized windows behind bottom panel"
date: 2008-12-07
forum: General Help
---

### Post by fubbleskag on 2008-12-07
**before i begin, i'd like to apologize if this (a) has already been asked/answered (i searched but was unable to find anything) and/or (b) is in the wrong forum.**

i would very much like to find a way to force maximized windows to take up the full area of the screen, ignoring the space that my bottom panel is taking.

*i am aware that i can set the panel to autohide, but this is not what i'm looking for.* i have removed the top-panel and moved my bottom-panel into the compiz widget layer. whenever i switch to the widget layer, all my maximized windows resize to adjust for the "new" presence of the bottom-panel. when i switch out of the widget layer, the maximized windows all return to the full desktop area.

this is only an aesthetic nuisance, as all my widgets are set to be on top and completely cover the desktop area on their own, so i'm not using any of the maximized windows while the widget layer is active, but i was surprised not to find any simple solution for this after a few days of googling.

i did try messing about with xprop, and after finally learning how to set the value of _NET_WORKAREA with the proper -f format, thought i had it fixed - but that didn't actually do anything.

thanks in advance for any suggestions

---

### Post by alexyz on 2008-12-14
Not exactly what you want, but a couple options.  

You can "float" the panel instead of having it at the bottom or top edge of the screen.  If you do that it no longer constrains maximized windows.  But since it's on top it gets in your way.  I attached a screenshot showing my desktop - I can maximize windows to take up the entire screen.

Another option is, in panel properties turn on "show hide buttons."  Then if you click the arrow the panel slides out of the way, and no longer constrains maximized windows. 

HTH.

---

### Post by fubbleskag on 2008-12-14
hmm, this could almost work. floating seems to require disabling expand, which i can likely live without, but i can't seem to float any closer than 49px to an edge without it jumping to the edge - anyway to overcome that?

thanks!

---

### Post by alexyz on 2008-12-14
> **fubbleskag said:**
> but i can't seem to float any closer than 49px to an edge without it jumping to the edge - anyway to overcome that?

Not that I can figure out.  I looked into it a while ago.  I'd prefer it just a little closer to the edge of the screen.  

slightly annoying ...

---

### Post by Danstroem on 2010-10-27
> i did try messing about with xprop, and after finally learning how to set the value of _NET_WORKAREA with the proper -f format, thought i had it fixed - but that didn't actually do anything.fubbleskag, could you please write the command here? I try to set the property with xprop for a different issue and I can not find any information how to do it with the correct -f parameter...

---

