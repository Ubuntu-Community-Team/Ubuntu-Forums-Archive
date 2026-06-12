---
title: "Unity2D Launcher Settings"
date: 2011-10-19
forum: Desktop Environments
---

### Post by KoopaTroopa on 2011-10-19
So I'm getting used to the new Unity2D interface but I still have some preferences that I'd like to alter to do with the launcher. I've gone to compiz settings manager and changed what I want but they don't seem to have actually taken place.

I've opened terminal and said 'compiz --replace' and now there's a second launcher (the other one is still there) which has listened to the unity plugin settings that I changed. But there is no longer any title bars. I've attached a picture of my desktop so you can actually see what's going wrong if you wish. So how do I stop the old launcher and get the title bars back?

---

### Post by KoopaTroopa on 2011-10-20
Anyone know how to fix this?

---

### Post by ACGarib on 2011-10-20
Unfortunately, Unity-2D is not as customizable as normal Unity. You need to install the program 2D-Desktop Settings to customize Unity-2D.

Compiz Settings Manager is for compiz, but since Unity-2D is not based on compiz, it has no effect, as you have found out.

If you switch to regular Unity, you can customize your settings via compiz settings manager.

---

### Post by KoopaTroopa on 2011-10-20
> **ACGarib said:**
> Unfortunately, Unity-2D is not as customizable as normal Unity. You need to install the program 2D-Desktop Settings to customize Unity-2D.

Compiz Settings Manager is for compiz, but since Unity-2D is not based on compiz, it has no effect, as you have found out.

If you switch to regular Unity, you can customize your settings via compiz settings manager.

Ah thanks a lot finally I can stop the launcher from hiding away. There's one other thing I don't know if you could help me with. At times when I'm doing some work on the computer I'm going to be switching from window to window. So having the launcher always on screen is ideal. But other times when I may be browsing the web for awhile I'd like the full screen back. Can I set a short cut key to toggle between 'always show' and to 'dodge windows'? Thanks for helping!

---

### Post by ACGarib on 2011-10-22
This article may help

[http://shuffleos.com/3126/how-to-configure-unity-2d-launcher-auto-hide-behavior-in-ubuntu-11-10/](http://shuffleos.com/3126/how-to-configure-unity-2d-launcher-auto-hide-behavior-in-ubuntu-11-10/)

First, try installing dconf-editor as per the article:
```
sudo apt-get install dconf-tools
```

I'm not a linux expert, but you could probably just go to "keyboard" (type that into the dash search bar) then go to "custom shortcuts" and make two custom shortcuts, one to enable auto-hide, and one to disable.

Write your custom shortcuts by pasting the following into the command part of a custom shortcut that enables auto-hide:

```
dconf write /com/canonical/unity-2d/launcher/use-strut true
```

If it works, then try making the other shortcut. (Do the same thing, but the command ends in "0" instead of "true")

---

