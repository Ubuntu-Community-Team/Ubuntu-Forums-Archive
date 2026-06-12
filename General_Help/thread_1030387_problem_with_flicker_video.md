---
title: "problem with flicker video"
date: 2009-01-04
forum: General Help
---

### Post by jarco5000 on 2009-01-04
When I enable any desktop effects in ubuntu I experience very annoying flikkering video effects in my totem and vlc media player. When i disable the effects it all runs very well.
I have a ati radeon 3850.
Anyone can help me solve this problem?

---

### Post by Brainonska511 on 2009-01-04
I actually have the same problem I have desktop effects turned on.  I was browsing some other thread and ran across this:

"For VLC, click on the Settings tab and go to Preferences. On the new window check the Advanced Options box. Now browse the three menu on the left and go to Video>Output Modules. Use the drop down box on the left to select X11 Output."

For my version of VLC, Preferences is under the Tools menu.  Changing the output to X11 on my machine has stopped the flickering when desktop effects are turned on.

---

### Post by wootah on 2009-01-04
> **jarco5000 said:**
> When I enable any desktop effects in ubuntu I experience very annoying flikkering video effects in my totem and vlc media player. When i disable the effects it all runs very well.
I have a ati radeon 3850.
Anyone can help me solve this problem?
Long story short, ATI driver's have an issue with multiple OpenGL windows along with compositing (try enabling desktop effects, and preview a OpenGL screen saver).

The proposed fix will be with DRI2, but there graphics backend memory management has changed, yadda yadda. It gets a little complicated.

Anyways, quickest fix is as mentioned above. Disable desktop effects, or change rendering method directed through X. This is be much slower (ie: use more processor power) but it will be unnoticeable with a fast computer).

---

### Post by jarco5000 on 2009-01-04
Well that's working for vlc. Thanks. (at least i can watch movies now :D)

Is there a possibility to do this system wide. totem and others are experiencing the same problems.

---

### Post by stderr on 2009-01-04
Please see [this]("http://ubuntuforums.org/showthread.php?t=1009239") thread :)

---

