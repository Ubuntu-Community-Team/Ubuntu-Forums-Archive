---
title: "Using the mouse scroll wheel at edge of screen to switch workspaces..."
date: 2009-11-08
forum: Desktop Environments
---

### Post by residualbit on 2009-11-08
This was the default behaviour for the last few releases of Ubuntu and it doesn't appear to be for Karmic. What happened? That was really handy. Anyone know how I can get that functionality back?

---

### Post by EvilZero65 on 2009-11-09
I was just wondering where this went to in karmic too. The best way I could figure out how to get it to work is under:

Compiz Config Settings Manager > Viewport Switcher > Desktop-based Viewport Switcher > Move Prev

and set that to Button4, which on my mouse is scroll wheel up and Move Next to Button5, scroll wheel down.
That will work on the desktop, but if you want to switch with other windows fullscreen, set
 
Rotate Cube > Bindings > Rotate Left to <LeftEdge><RightEdge>Button4 and Rotate Right to <LeftEdge><RightEdge>Button5.

That should work, minus the viewport switcher window coming up like it used to.

---

### Post by hariks0 on 2009-12-19
It is under Desktop --> Viewport Switcher-->Desktopbased viewport switcher tab. Change the values of Move Next to Button4 and Move Prev to Button5.

---

### Post by wpurcell on 2010-12-11
Thanks Hariks0!

---

