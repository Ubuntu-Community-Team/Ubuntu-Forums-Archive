---
title: "KDE Remote Desktop: connection OK, but just a black screen"
date: 2005-09-13
forum: Desktop Environments
---

### Post by coaxx on 2005-09-13
Hi all,
after I connect with vnc (tightvnc/realvnc) from a windows mashine to my KDE Kubuntu Desctop, I only can see a black screen after it askes my for user/password.

Settings in Kubuntu seem to be ok since a can successfully connect (<ip>:0)

Any hints?

---

### Post by fortytwo on 2005-09-13
[QUOTE=coaxx]Hi all,
after I connect with vnc (tightvnc/realvnc) from a windows mashine to my KDE Kubuntu Desctop, I only can see a black screen after it askes my for user/password.

Settings in Kubuntu seem to be ok since a can successfully connect (<ip>:0)

Any hints?[/QUOTE]
 You're connecting to display 0?  I think I've seen people talk about how that may not be possible...? I'm not sure...but I've had this problem many times in the past when connecting to display 1.  What I had to do was mess with the ~/.vnc/xstartup file (I'm using tightvnc).  Mine ended up looking like this:

#!/bin/sh
unset SESSION_MANAGER
startkde &


Obviously, substitute 'startkde' with whatever manager you're using.  Good luck.

---

### Post by Divan Santana on 2005-09-17
[QUOTE=coaxx]Hi all,
after I connect with vnc (tightvnc/realvnc) from a windows mashine to my KDE Kubuntu Desctop, I only can see a black screen after it askes my for user/password.

Settings in Kubuntu seem to be ok since a can successfully connect (<ip>:0)

Any hints?[/QUOTE]

use freenx / nxserver instead

---

