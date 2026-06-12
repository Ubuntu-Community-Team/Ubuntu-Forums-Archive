---
title: "Metacity lost its Xinerama awareness."
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by sws26 on 2007-10-19
Since an upgrade to Gutsy Metacity seams to have lost all awareness of the
xinerama extensions (using twinview). I like having maximised windows not span both
of my monitors and also having independent window lists for each monitor.

Is there anyway to re-enable this?

---

### Post by ky13 on 2007-10-19
XFCE (upgraded in Xubuntu) did as well.  Neither hardware nor xorg.conf changed.  Any ideas?  I did get a notice, the first time I logged in about Xgl.  A clue?

---

### Post by sws26 on 2007-10-19
I note in another thread that compiz has the same problems but it supports artificially
setting display windows by disabling auto-detect. You still end up with panels spanning
monitors and you can't get a window list for each monitor but at least it's a step up
from what I have now.

I get the feeling the problem is with X, probably something to do with XGL as you suggest.

---

### Post by ky13 on 2007-10-19
I fixed it by uninstalling Xgl.

You might be able to fix it by editing /etc/X11/Xsession.d/98xserver-xgl_start-server to use -xinerama instead of +xinerama, but I recommend just uninstalling it.

---

### Post by sws26 on 2007-10-19
Tried adding the -xinerama option, didn't work. In the end uninstalled Xgl and now it's working again, thanks for your help.

---

