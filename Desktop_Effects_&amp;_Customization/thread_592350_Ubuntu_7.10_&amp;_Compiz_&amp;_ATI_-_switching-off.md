---
title: "Ubuntu 7.10 &amp; Compiz &amp; ATI - switching-off of the screen"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by yalex2000 on 2007-10-26
Ubuntu 7.10 & Compiz & ATI - switching-off of the screen in 10 minutes during viewing video. 
It occurs only in that case if is started XGL, and without it all &#1086;&#1082;. 
What to do?!?!?

---

### Post by yalex2000 on 2007-10-26
What does nobody know? :(

---

### Post by Mike Maximus on 2007-10-26
I had this problem a few days ago.  Searched around and found the following:

Add this to /etc/X11/xorg.conf

Section "ServerFlags"
        Option      "blank time" "0"
        Option      "standby time" "0"
        Option      "suspend time" "0"
        Option      "off time" "0"
EndSection

Note that your monitor will never shut itself off with these settings.

---

