---
title: "Doesn't run Blender properly"
date: 2009-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by confubar on 2009-12-07
New dell inspiron 15n.. Ubuntu 9.04
Installed Blender using synaptic. Images double on top of each other as soon as I resize windows and it takes the force-application-to-quit widget to get out. (the window will gradually disappear as I mouse around on it... I completely removed and installed again.. no better.
Does anybody have any idea why my system won't handle blender properly.

---

### Post by confubar on 2009-12-08
Is it possible that graphics card/drivers could be cause of doubling/ blurring of Blender interface?[-o<[-o<
The laptop is supposed to have Intel Graphics Media Accelerator X4500HD... the inspiron 15n comes with ubuntu installed and is supposed to come with appropriate drivers for the hardware that dell puts in the machine. Note that the blurry doubles don't necessarily happen when one is doing something fancy... the windows, menus, cursor are screwed

---

### Post by gomyhr on 2009-12-08
Yes, you're right. There are numerous bugs in mesa and xorg in Jaunty that prevent blender from working properly. I think we got all the show-stoppers fixed for Karmic. For more details, see [http://www.blender.org/forum/viewtopic.php?p=74985#74985](http://www.blender.org/forum/viewtopic.php?p=74985#74985) .

---

### Post by confubar on 2009-12-09
> **gomyhr said:**
> Yes, you're right. There are numerous bugs in mesa and xorg in Jaunty that prevent blender from working properly. I think we got all the show-stoppers fixed for Karmic. For more details, see [http://www.blender.org/forum/viewtopic.php?p=74985#74985](http://www.blender.org/forum/viewtopic.php?p=74985#74985) .

Thanks, gomyhr, this is the best lead yet.

---

