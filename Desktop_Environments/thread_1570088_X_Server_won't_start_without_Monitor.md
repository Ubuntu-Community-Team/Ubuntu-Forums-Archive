---
title: "X Server won't start without Monitor"
date: 2010-09-07
forum: Desktop Environments
---

### Post by M1GEO on 2010-09-07
I've seen many references to people with similar problems to this, but I wasn't able to get it working...  Here's the problem:

I wish to have a headless server, which I can control via VNC.  _With a monitor connected_, the machine powers up, starts X11, and then starts some programs.

However, these programs, although graphical, don't require a monitor to be connected, and I can maintain the machine via VNC.  I have x11vnc configured to run, providing the X server starts, VNC server starts and my programs run perfectly. **_HOWEVER, without the monitor, X11 doesn't start._**

Any information on how to get X to start **_without the monitor_** would be really helpful.  

Kind Regards,
George Smart, M1GEO.

---

### Post by M1GEO on 2010-09-08
For completeness, I found an ideal solution to my problem here:

[http://ubuntuforums.org/showpost.php?p=9759320&postcount=15](http://ubuntuforums.org/showpost.php?p=9759320&postcount=15)

---

