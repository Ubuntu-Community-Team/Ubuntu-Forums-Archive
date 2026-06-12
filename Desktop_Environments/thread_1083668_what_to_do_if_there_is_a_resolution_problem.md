---
title: "what to do if there is a resolution problem"
date: 2009-03-01
forum: Desktop Environments
---

### Post by aliboy on 2009-03-01
current maximum resolution is only 600x400 (in change screen resolution menu). what to do to bring out the option of up to 1440x900. visual effects is already ok, its just that the screen resolution is only that low.:P:popcorn:

---

### Post by thtrgremlin on 2009-03-01
have you tried```
gnome-display-properties
```This should allow you to change screen resolutions. or are you saying that the given resolution is your only option?

---

### Post by aliboy on 2009-03-01
the list is only from 320x240 to 640x480, no more higher resolution than that. can anyone help me or remote my pc just to fixedthe screen resolution problem...

---

### Post by hictio on 2009-03-01
> **aliboy said:**
> the list is only from 320x240 to 640x480, no more higher resolution than that. can anyone help me or remote my pc just to fixedthe screen resolution problem...

Check this thread: [help please with resolution ibex](http://ubuntuforums.org/showthread.php?t=975452&page=2)

It looks to me like to have to edit the '/etc/X11/xorg.conf' file, adding the desired resolutions to the 'Modes' line on the 'Screen' section.
Maybe even you'll have to add the vertical and horizontal refresh rate for your monitor as well.

---

### Post by aliboy on 2009-03-02
please indicate steps on how to edit /etc/X11/xorg.conf
when i tried to paste that code in terminal it says  Permission denied.

---

### Post by aliboy on 2009-03-02
the problem is already solve... 
i just go to add/remove and add "screen and graphics" after that i was able to select the video card i have and monitor model then everything are OK:lolflag::guitar::popcorn:

---

