---
title: "Unity does not work properly, only Unity 2D"
date: 2012-05-18
forum: Desktop Environments
---

### Post by fizikz on 2012-05-18
I have upgraded to 12.04 and have tried Gnome Shell, Gnome classic, Unity, and Unity 2D. All, but Unity work fine. If I log in using Unity, the window decorations, the dock and the notification strip at the top of the screen are all missing. Aside from that, I can still use keyboard shortcuts to launch a terminal, etc. I have nVidia's proprietary drivers installed and working. The unity support test shows that the system is 3D compatible. Suggestions?

---

### Post by ajgreeny on 2012-05-18
Perhaps your nvidia card is not capable of running unity3D; what card is it?

---

### Post by fizikz on 2012-05-18
```
$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7700/PCIe/SSE2
OpenGL version string:  2.1.2 NVIDIA 295.53

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

I have a Go 7700 and the unity support test reports that 3D should be supported.

---

### Post by wilee-nilee on 2012-05-18
Check the additional drivers app for any waiting for install.

---

### Post by fizikz on 2012-05-18
The video drivers are the most recent ones available. The nvidia drivers were manually installed and the 'additional drivers' app only messes up the system. Besides Unity, other applications or DEs needing hardware acceleration are working fine.

---

### Post by wilee-nilee on 2012-05-18
> **fizikz said:**
> The video drivers are the most recent ones available. The nvidia drivers were manually installed and the 'additional drivers' app only messes up the system. Besides Unity, other applications or DEs needing hardware acceleration are working fine.

If you install the drivers from nvidia, a update in drivers can set them off I believe, not an area I'm really knowledgeable in though, I have never had a nvidia card.

Tweaking compiz as well causes problems if you don't know what you are doing, not saying you don't just commenting.

---

### Post by fizikz on 2012-05-18
Yes, the manual installation causes the drivers from the Ubuntu repository not to work well. This is why I don't use the 'additional drivers' app. One day if I do a clean install I'll use it. In the meantime, the manually installed drivers are working fine, and it's just Unity that is having a problem running. I'm not even sure that it is a video driver issue.

---

### Post by mutap on 2012-05-18
Did you by any chance played with Compiz Settings Manager?
I had the same issue, Ati card, unity support test was all yes, yes, yes, driver was ok but I had only wallpaper when I logged to Unity.
I reseted Compiz settings to default and after that it was all fine.

---

### Post by fizikz on 2012-05-18
I have Compiz Settings Manager and I have changed some settings in there previously. I would hope not to need to reset it completely to default. Would you have a clue about which settings might cause problems? What you say makes sense. This could be promising.

---

### Post by mutap on 2012-05-18
Well I just tried to enable Cube but it didn't work.

So I checked all of these settings ( Composite, Gnome Compability, OpenGLDesktop Wall, Expo, Ubuntu Unity Plugin, Viewport Switcher, Window Decoration, Png, Bailer, Compiz Library Toolbox, Detection, Mouse position polling, Regex Metching, Session Menagment, Workaraunds, Grid, Place Windows, Move Window, Resize Window, Scale, Static Application Switcher, Window Rules ) and this did the trick.

Other way is to start CCM, go to Preferences and then to Reset to defaults(but I haven't tried it this way).
Or from console -> [FONT=Arial]gconftool --recursive-unset /apps/compiz-1[/FONT]
[FONT=Arial]Haven't tried this also, it should work in theory :)

These Unity problems with Compiz are probably reason why CCM is not in Ubuntu by default and why you'll get warning when you start it. :)

I won't be playing with CCM any more for sure. :)
[/FONT]

---

### Post by wilee-nilee on 2012-05-18
The thing about trying drivers and getting it set up correctly is to remove one before installing another. Seems from reading here you have piled them up, not sure though. A upgrade needs the drivers purged and reinstalled.

---

### Post by fizikz on 2012-05-18
My list of CCSM settings/plugins is quite similar, but not identical. The Ubuntu Unity plugin was one that was not enabled. I tried enabling it, but it did not help in Unity loading. However, in gnome, I ended up having the Unity launcher... So, I disabled it as it was before. I don't think I want to try too many of those settings, in case I mess it up further. 

When installing the latest nvidia driver, the installer first uninstalled the older one. I'm not sure how good a job it does, but that was part of the process.

---

### Post by wilee-nilee on 2012-05-18
> **fizikz said:**
> My list of CCSM settings/plugins is quite similar, but not identical. The Ubuntu Unity plugin was one that was not enabled. I tried enabling it, but it did not help in Unity loading. However, in gnome, I ended up having the Unity launcher... So, I disabled it as it was before. I don't think I want to try too many of those settings, in case I mess it up further. 

When installing the latest nvidia driver, the installer first uninstalled the older one. I'm not sure how good a job it does, but that was part of the process.

I would run in the 3d from crtl-f2 unity --reset this will reset the whole 3d setup and probably the 2d as well.

Can be run from the terminal as well, and probably from the 2d as well.

There are other commands to reset compiz as well if this does not do it.

Take a look at askubuntu for these other commands

---

### Post by fizikz on 2012-05-19
In CCSM -> Preferences -> Profile I noticed that it was set to Default. In the drop-down menu, there was also a "Unity" entry. When I selected Unity there, and did unity --replace, it worked!

So far 2D and 3D look identical, so I was a bit unsure of whether 3D was working or not, but now on the login page when I choose "Ubuntu" or "Ubuntu 2D" it works fine and logs in properly, with window decorations in place. 

Thanks for all your help!!

---

