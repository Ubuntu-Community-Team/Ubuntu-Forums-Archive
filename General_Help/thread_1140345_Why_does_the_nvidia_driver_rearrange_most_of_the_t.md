---
title: "Why does the nvidia driver rearrange most of the taskbar icons?"
date: 2009-04-27
forum: General Help
---

### Post by Raskula on 2009-04-27
[img]http://i44.tinypic.com/24vuumx.jpg[/img]


Every version of ubuntu, I change my resolution with nvidia-settings and it does this. Why?

---

### Post by mcduck on 2009-04-27
it's not nvidia driver. Simply changing the resolutions..

To explain it a bit, the location of applets in panels is defined as pixels from the left edge of the panel. When you switch to low resolution, the applet locations are changed so that they fit inside the panel. When you change to higher resolution, the applets try to keep the locations they are set to use, while the panel itself expands further to right. As a result you end with panel applets in strange locations.

There are couple of ways to avoid this:

First, try to avoid switching between high and low resolutions.. ;)

Second, set the resolution as high as you'll ever use, move the applets to correct locations and then lock them in place. With any luck they should now keep their locations even when switching between different resolutions.

Third, it *is* possible to set applets to define their location from the right end of the panel instead of the left end. However you need to do this manually with the gconf-editor. But if you do this, and set all the applets you want to stick to the right in the panel to define their locations as distance from the right end of the panel the problem should disappear.

In the end, it's usually easiest to keep the applets unlocked and just use middle mouse button to drag them to correct places after changing the resolution.

---

### Post by Raskula on 2009-04-27
Alright thank you, I didn't know that it was just the fact of the resolution changing.

---

### Post by asdir on 2009-05-11
I have the same problem, even though switching from 1 to 2 monitors and back only increases the height but not the breadth (one monitor is "on top" of the other). Shouldn't the icons stay in the same place then, since their distance to the left (or right) side stays the same?

Thanks for the tipp with the middle mouse button. I had never heard that one before. ;-)

---

