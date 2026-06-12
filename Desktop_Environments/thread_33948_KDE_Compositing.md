---
title: "KDE Compositing"
date: 2005-05-12
forum: Desktop Environments
---

### Post by Staesys on 2005-05-12
Okay, how do I turn this off? I tried it out just to see what it looks like, and now I can't get it to go away. I wouldn't mind if it it weren't slower than snot, and this is on a 2.2 GHz computer.

I've turned off all shadows, translucency and effects I can find, but yet, every time I start KDE it comes back. The only way I can get it to go away is remove the compositing lines from xorg.conf and then it complains about it when it starts. I try to run kompmgr it says a compositing manager is already running.

-Paul

---

### Post by Jesus Franco on 2005-05-12
Uncheck the settings you checked to enable it. In the kde control panel under Look&feel its somwere there. I might be wrong I haven't used kde in a long time.

---

### Post by ludi on 2005-05-12
[QUOTE=Staesys]Okay, how do I turn this off? I tried it out just to see what it looks like, and now I can't get it to go away. I wouldn't mind if it it weren't slower than snot, and this is on a 2.2 GHz computer.

I've turned off all shadows, translucency and effects I can find, but yet, every time I start KDE it comes back. The only way I can get it to go away is remove the compositing lines from xorg.conf and then it complains about it when it starts. I try to run kompmgr it says a compositing manager is already running.

-Paul[/QUOTE]

You must have enable the hardware aceleration first.
Everything in http://www.ubuntuforums.org/showthread.php?t=20769&highlight=composite"  thread.
Incluing the nvidia binary drive issue.

---

### Post by Staesys on 2005-05-13
Thank God! I finally found the setting.

KDE Control Center -> Desktop -> Window Behavior -> Translucency 

and unselect Use translucency/shadows

Thanks guys!

-Paul

---

