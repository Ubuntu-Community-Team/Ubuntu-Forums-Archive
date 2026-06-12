---
title: "Resolution Problems Driving Me Mad"
date: 2008-01-27
forum: Desktop Environments
---

### Post by dieg0 on 2008-01-27
So, for a while now I have been trying to get into using Ubuntu, but there is a problem with my resolution. I have a wide screen monitor with a 1680x1050 resolution and an ATI Radeon X1900 video card. So I had finally set up my wireless card but when i tried to fix my resolution problems i failed miserably. I've considered starting over from scratch but i thought maybe you guys could help me out of my rut that i am in and get me up and running again.

   So right now when i try to use Ubuntu the display makes it impossible. The screen it copy multiple times on top of the screen and it's very distorted.
[[IMG]http://img516.imageshack.us/img516/9594/dscn0044vl4.th.jpg[/IMG]](http://img516.imageshack.us/my.php?image=dscn0044vl4.jpg)
When i move my mouse to see it moving in about 8 places. Keep in mind that I can't use this anymore to fix it, so I think it'd have to use recovery mode. If it's any help to helping me, before I had tried changing the resolution I had tried installing the drivers ATI provides. It installed but it told me to enter a command to configure it and it said it failed. I restarted anyways and it was just the same when i started it up again. I tried accessing the Catalyst control center but it wouldn't do anything. So I went to the administration and tried changing my video card to an ATI one listed. When i logged out it became the reason why I'm here.

If you can help, I swear I'd kiss you because this has been a problem for me for so long.

Thanks, Diego.

---

### Post by MasterJS on 2008-01-27
try ```
 sudo dpkg-reconfigure xserver-xorg
``` That should help you remake your Xorg.conf file. This is used for your graphics and everything else. It'll take you through different steps asking you for you video card driver (which for ATI will be either ati or radeon, not sure which one is for yours), your keyboard language settings, your resolution settings, and other things like that that i can't remember at the moment. Go through that, and if it doesnt fix your problem, post back here.

---

### Post by dieg0 on 2008-01-27
Didn't work =\. When i put it in it said something about "conflicting actions"

---

### Post by MasterJS on 2008-01-27
what did you have running at the moment?

---

### Post by dieg0 on 2008-01-27
> **MasterJS said:**
> what did you have running at the moment?

What do you mean by running? I'm in recovery mode so I don't think I'm running anything other than the console.

---

### Post by dieg0 on 2008-01-28
Does anyone else please have some suggestions on what I can do?

---

