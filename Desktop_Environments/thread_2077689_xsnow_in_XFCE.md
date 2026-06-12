---
title: "xsnow in XFCE"
date: 2012-10-29
forum: Desktop Environments
---

### Post by The Cog on 2012-10-29
Xsnow doesn't snow on Xubuntu 12.10. I get the trees, but Santa appears and disappears after a short time, and I don't get any snow at all. This is global warming gone mad! Does anyone know how to get xsnow working?

---

### Post by howefield on 2012-10-29
For fun, I installed xsnow but get something slightly different, I do get snow however it doesn't fall - it just collects at bottom of screen. See the odd flake going down the edge of the screen.

I'm guessing it is falling, but just can't see it until it hits the bottom of the screen.

---

### Post by westie457 on 2012-10-29
Also for fun tried xsnow in ubuntu 12.04.

First attempt got me snow appearing at the bottom of the screen and trees and reindeer. This was using the intel graphics chip.

2nd attempt. Invoked the Nvidia chip with ```
optirun xsnow
```
Got snow falling down the right side of the screen with trees all over and the reindeer. See screenshot.

---

### Post by The Cog on 2012-10-29
Sorry, I lied. I do get snow collecting at the bottom of the screen. And on close inspection, there is the occasional falling flake on the right hand edge, as howefield describes. But not the falling snow as it normally is.

I suspected changes to X causing it, but xpenguins still works normally so I don't think it's a general X problem.

---

### Post by bluenode on 2012-11-27
Looks like compositing has to be disabled for the holidays -- I turned it off and the seasonally essential xsnow is working properly.  Ahh ... now it's **really** xmastime!

---

