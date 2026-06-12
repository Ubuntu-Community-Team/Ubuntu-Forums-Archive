---
title: "Cursor stuck after game crash."
date: 2008-01-03
forum: Gaming &amp; Leisure
---

### Post by JillSwift on 2008-01-03
After Enemy Territory:Quake Wars crashed on me today, my mouse cursor was stuck. I assume that the mouse input was still "captured" by Quake.

Is there a way to unstuckify it? Besides restarting (ctrl-alt-bkspce) X, which was my "solution" of the moment?

Ubuntu 7.10, Gnome 2.20.1
PNY nVidia 7600gt

---

### Post by happyhamster on 2008-01-03
Try changing to a different workspace (ctrl-alt-right arrow) and back again (ctrl-alt-left arrow).

Or switch to a virtual console (ctrl-alt-F3) and back again (ctrl-alt-F7).

Or: first take keyboard and mouse control from the X server using Alt+SysRq+r (pressing those simultaneously can be quite a challenge BTW :) ), then switch to a console and back again.

Success, and let us know if any of those work.


[edit: changed "right" into "left" and vice versa :) ]

---

### Post by JillSwift on 2008-01-04
Printed your post and stuck it on my cork board. Next time one of my games crashes, I'll post the results =^_^=

---

### Post by klightspeed on 2008-09-20
Switching between PTYs did not work.
SysRQ-R did not work.

_Starting a game that captured the mouse **worked**_

---

### Post by Sockerdrickan on 2008-09-20
reconnect the mouse manually IRL

---

