---
title: "how to add modeline? when i try i cant boot."
date: 2008-07-08
forum: Desktop Environments
---

### Post by dracule on 2008-07-08
I am in Fluxbuntu right now, but to get my proper screen res i have to do this:

xrandr -s 1440x900

if i simply select 1440x900 from the screen resolution picker, it is very weird and is kind of a "zoomed in" image, where it only shows part of the desktop, and when my cursor is near the edge it scrolls over. incidentally it does this for ALL resolutions when chosen out of the resolution picker in fluxbox.

I asked someone how to fix this and they said add a modeline. so i looked up a modeline generator, but the person had to go so i nvr really knew how to use it. this is what i got back out of it:

Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946

and so the thing said to put it in your Display and Monitor section. so i did, but my computer would not boot (it wouldnt even say "X could not be started" and take you to command prompt like if you corrupt a xorg.conf file normally).

i just want to use my 1440x900 res when i boot, w/o doing xrandr

---

### Post by markjensen on 2008-07-08
Worst case, add your xrandr line into your fluxbox startup file.

---

