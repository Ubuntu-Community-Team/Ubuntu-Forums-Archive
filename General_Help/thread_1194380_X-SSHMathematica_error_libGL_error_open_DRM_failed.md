---
title: "X-SSH/Mathematica error: libGL error: open DRM failed"
date: 2009-06-22
forum: General Help
---

### Post by chellrose on 2009-06-22
I'm trying to use Mathematica 6 on a remote machine using ssh -X.  When I start Mathematica on the remote machine, I see this error:

libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering

This causes the GUI to be really, painfully, insanely slow.

I did a Google search and a search on this forum, and all I could find was a bunch of suggestions to add

```

Section "DRI"
    Mode 0666
EndSection

```

to my /etc/X11/xorg.conf.  I did that, and tried restarting the X server, and rebooting, all to no avail.

Does anyone have any other suggestions?

Thanks! :D

---

