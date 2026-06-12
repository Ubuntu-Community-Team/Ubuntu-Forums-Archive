---
title: "how to disable compiz on start-up?"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by bittergourd on 2007-10-31
hi,
i am running gutsy on laptop (with X3100 graphics).  there is a dri-related bug of i915 graphics chip which wakes up cpu frequently.  obviously this is unwanted if one wants to save power on a laptop.  i am aware that putting "nodri" option in the xorg.conf file will disable 3D features of the graphics card, which evidently solves the problem.  however, it would be more convenient to have options at the log-in stage where i can choose to save power or to have eye-candy.  

is there a way that different start-up sessions load different xorg.conf files?  or a start up script like those in the early ages of XGL would solve the problem?

- yi

---

### Post by Forlong on 2007-10-31
Hm... sounds like an interesting issue to solve.
This is what I could get out of my head after a minute of thinking about it:

You could boot into shell (instead of GDM - don't know how to achieve that right now but I'm confident that it's possible without removing GDM completely) and start a script from there, that takes care of the xorg.conf switching (that part part is quite easy) and finally start X manually.

---

