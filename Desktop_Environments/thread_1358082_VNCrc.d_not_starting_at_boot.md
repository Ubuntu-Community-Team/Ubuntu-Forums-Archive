---
title: "VNC/rc.d not starting at boot?"
date: 2009-12-17
forum: Desktop Environments
---

### Post by buee on 2009-12-17
I have a bit of a peculiar situation going on here.  I've put 3 different scripts in to rc.d, which doesn't report an error when I execute ```
update-rc.d scriptname defaults
``` When I do that again, it does kickback an error.  But these scripts never start at boot.

Also, for some random reason, if I start up the machine with a monitor plugged in, I can VNC to it no issue.  If I start up the machine without a monitor plugged in, I get my connection refused via VNC.  But, I can start it with a monitor, unplug the monitor, and VNC works like a champ.  Is my UBU hosed?

---

