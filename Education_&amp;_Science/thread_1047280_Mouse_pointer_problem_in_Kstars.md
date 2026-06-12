---
title: "Mouse pointer problem in Kstars"
date: 2009-01-22
forum: Education &amp; Science
---

### Post by skywatcher on 2009-01-22
I am starting this thread in desperation, hoping that someone has a solution to the problem.

I installed Kstars on Intrepid, but found that the mouse pointer is invisible over the star map area, but not over the rest of the interface.  After searching around, I found what seemed to be a solution on another forum -- that was to place the following line in the "Device" section of /etc/X11/xorg.conf:

```
Option "AccelMethod" "XAA"
```

This solved the problem, but when I tried to view a video, it wouldn't work, so I had to remove the line again, leaving me with the invisible pointer in Kstars once again.

Since I'm also having trouble getting SkyChart installed on Intrepid (see astronomy software thread on this forum), I'm really stuck.

Help, anyone?

---

### Post by cdyson37 on 2009-02-03
I'm having this problem too (running kstars within gnome). Any ideas?

Thanks,

Charlie

---

### Post by Falconnn on 2009-06-05
> **cdyson37 said:**
> I'm having this problem too (running kstars within gnome). Any ideas?

Thanks,

Charlie

To be fear, I've replaced Ubuntu with Kubuntu for this specific reason,but in KDE 4.2.2 (I think) - Kubuntu 9.04 there is same problem... Any Ideas? :(:confused:

---

### Post by macabrem on 2009-10-05
I'm having this same problem.  Has anybody found a fix?

---

