---
title: "Reset user X settings"
date: 2009-05-09
forum: General Help
---

### Post by gunksta on 2009-05-09
Although I am glad that X setup is becoming more nuanced and dynamic, it does make it more complicated for us old timers.

I have a Linux box attached to a LG flatscreen TV.

My xorg.conf is working fine. When I start the computer GDM works just fine. In fact,  _was_ working perfectly, until I muddled with things.  Now, when I log in, the screen shows an error "Invalid Format". 

I Used gnome-display-properties, to increase the resolution of the screen. When I tried out my settings, the monitor announced Invalid Format. I waited and for some reason it did not reset to the former setting.

That's when my problems really began.

AFAIK, gnome-display-properties uses XRandr to change user-level display settings, but I can't find any way to nuke the changes and bring the account back to how it was before I muddled with it.

Suggestions are greatly appreciated, but I do want to stress that my xorg.conf file is not the problem. My other account works just fine.

Thanks

---

### Post by gunksta on 2009-05-09
I hate it when I ask for help and then solve the problem 2 minutes later.

xrandr -s 0

worked a charm.  Thanks me.

---

