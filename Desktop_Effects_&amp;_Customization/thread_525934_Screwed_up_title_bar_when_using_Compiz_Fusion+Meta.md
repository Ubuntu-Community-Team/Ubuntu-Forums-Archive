---
title: "Screwed up title bar when using Compiz Fusion+Metacity as window decorator"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by rafaelcapanema on 2007-08-14
When using Compiz Fusion, I enable Metacity as the window decorator so I can set Ubuntu Studio's default theme. But there's a drawback: after some mouse movements, the title bar of maximized windows gets screwed up (see attached image). The buttons and the bar itself work normally, though.
Emerald themes look fine. I would use a port of Ubuntu Studio's theme, but I still haven't found it.
Any workarounds?

I have an nVidia GeForce 5200 and I'm using the last version of Compiz Fusion (even though I have experienced the same problem a long time ago, still on Beryl).

Thank you very much!

---

### Post by rafaelcapanema on 2007-08-15
Anyone?

---

### Post by interjaz on 2007-08-17
Same + black square insted of content
[http://ubuntuforums.org/showthread.php?t=527990](http://ubuntuforums.org/showthread.php?t=527990)

---

### Post by Hund on 2007-10-30
Same bug for me. :(

---

### Post by isecore on 2007-12-04
I have this problem as well. Very annoying, even though it doesn't affect anything else but the visuals of maximized windows. I experienced this same thing under Feisty when I ran Compiz Fusion as well, and tried to find a fix.

Several were suggested over on the Open Compositing forums but none worked for me, which makes it seem like a very strange bug.

---

### Post by Znort_Ubern00b on 2007-12-04
i had similarproblem, running feisty using 5200 geforce card entered the below in terminal and it sorted it...

i couldn't min,max or close as no bar was showing...

> sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

### Post by isecore on 2007-12-06
> **Znort_Ubern00b said:**
> i had similarproblem, running feisty using 5200 geforce card entered the below in terminal and it sorted it...

i couldn't min,max or close as no bar was showing...

I already (and would assume most people do as well) have 

```
Option          "AddARGBGLXVisuals"     "True"
```

set in my xorg.conf, which is (as far as I know) the same thing, yet my titlebars get corrupted when the windows are maximized.

---

