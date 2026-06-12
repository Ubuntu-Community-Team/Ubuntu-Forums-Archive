---
title: "Mouse buttons get lost after Intrepid update"
date: 2009-01-12
forum: General Help
---

### Post by jcollins@cs.umn.edu on 2009-01-12
I've been a satisfied Ubuntu user for several years. I recently updated my Dell Inspiron 530 from 7.10 to 8.04, used it for a few weeks to be sure it was stable, then updated again to 8.10. Now, once or twice per day it loses track of the mouse buttons and wheel. The on-screen cursor still follows the mouse, but window focus does not. The only way I've discovered to recover from this is to kill X using ctl-alt-backspace. At first I thought it had something to do with Firefox, but now I'm not so sure.

Here's what I've tried:
[LIST]
[*]I've looked through /var/log/* and cannot find anything that correlates with an incident.
[*]I've tried disconnecting and re-connecting the USB cable from the mouse. The mouse is detected and the cursor works afterward, but still no buttons and no focus.
[*]I've tried every key combo I can think of.
[/LIST]

My config:
Video: nVidia GeForce 8600
Mouse: Dell optical USB
Monitors: dual-head Xinerama, set up using the nVidia config tool. It's the same setup I used in 7.10 and 8.04.

---

### Post by dcstar on 2009-01-15
> **jcollins@cs.umn.edu said:**
> I've been a satisfied Ubuntu user for several years. I recently updated my Dell Inspiron 530 from 7.10 to 8.04, used it for a few weeks to be sure it was stable, then updated again to 8.10. Now, once or twice per day it loses track of the mouse buttons and wheel. The on-screen cursor still follows the mouse, but window focus does not. The only way I've discovered to recover from this is to kill X using ctl-alt-backspace. At first I thought it had something to do with Firefox, but now I'm not so sure.
.........

It also happens in my 8.04 system - some recent update has caused this problem but it seems it hasn't been pinpointed as yet.

---

