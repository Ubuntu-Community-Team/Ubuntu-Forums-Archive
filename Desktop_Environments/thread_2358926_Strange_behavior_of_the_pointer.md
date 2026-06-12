---
title: "Strange behavior of the pointer"
date: 2017-04-18
forum: Desktop Environments
---

### Post by jgrnst on 2017-04-18
Hello, few days ago I upgraded to Kubuntu 17.04 and since then, the mouse pointer behaves as if it has a square attached to it which covers a portion of the screen next to the pointer. What appears in that square depends on the previous position of the pointer. Then the pointer is left in the same place the square disappears. It is extremely inconvenient - for example, while typing, one must make sure that the pointer is parked sufficiently far from the text being typed; worst of all is selecting text with a mouse and scrolling.

I am not sure whether this is a KDE/Plasma or an Nviidia issue (I am using Nvidia 381 from ppa:graphic-drivers).

---

### Post by SeijiSensei on 2017-04-18
Have you looked in SystemSettings to see how the pointer is defined? On my 14.04 machine, it's in System Settings > Workspace Appearance > Cursor Theme.

---

### Post by jgrnst on 2017-04-19
This behavior does not depend on the cursor theme, if that is what you are asking. This invisible square cannot be a part of an intended definition because it is extremely annoying (for example, thanks to it I lost a very convenient functionality for editing formulas in TeX, namely I can no longer select a part of a formula with the mouse and move it to a different place - thanks to this wonderful pointer I never know where exactly the selection ends). Besides, I have never seen anything like that in previous versions (or in any other Linux distribution I ever worked with).

---

### Post by jgrnst on 2017-04-19
Here is a screenshot ([https://goo.gl/photos/3dJ1ZM19iij8C1eo7](https://goo.gl/photos/3dJ1ZM19iij8C1eo7)). Note the white square with .org in it (it shows a part of the previous webpage displayed in that window)

---

### Post by jagracar on 2017-04-25
Hi there,

I had exactly the same problem today. Changing the driver to the Nouveau one and rebooting worked for me.

---

### Post by jgrnst on 2017-04-25
I suspect that it might be an Nvidia problem. However, Nouveau has a lot of issues too; I have Kubuntu installed on a laptop which I often use with dual monitors. My past experience shows that Nouveau is very unreliable in such environment. It also used to have problems with suspending to RAM.

---

### Post by jgrnst on 2017-05-01
Tried changing to nouveau; it seems to be working, and I did not run into any issues so far. Thank you for sharing, I was thinking about trying nouveau, but probably would not try it if you did not post that it worked for you, as I had issues with nouveau in the past.

---

### Post by frank770504 on 2017-08-22
hi everyone

I met the same problem and solved this issue just a minute ago.

My kubuntu version is 16.04, not 17.04, and with a nvidia graphic driver.

I did two steps.

1. install the nvidia driver to the latest (nvidia-384)
2. change the "System setting -> Display and Monitor -> Compositor -> Rendering Backend" from openGL 2.0 to XRender

However I am not sure the first step is necessary, because the problem just fixed after I change the rendering backend.

---

### Post by niko_pl on 2017-08-24
Hi there,

changing the "Rendering Backend" worked for me. Thanks a lot [B][COLOR=#000000]frank770504
[/COLOR][/B][COLOR=#000000] [/COLOR][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][B][COLOR=#000000]
[/COLOR][/B]

---

### Post by rajatjain1998 on 2017-10-02
Solution for square box behind the cursor in Kubuntu.
Hello,
I also faced the same problem and find the solution for it.

According to me this problem is due to Nvidia driver.

1. Just go to the installed application and remove the Nvidia driver.

2. Then It will show you option to install the Nvidia driver in the system tray (if not restart your computer).

3. Then in driver install window you will see two options:
    a) Using NVIDIA binary driver- ... version 375.39 form ... nvidia 375(Recommended) [something like that]
    b) Using X.Org X server - Nouveau display driver from... [something like that]
 You have to choose the second option then install and reboot.

Thank You :)

---

### Post by jacekmw2 on 2017-10-12
Same problem on my Lenovo 540 laptop and 16.04 LTS.
 The nouveau driver is installed by default, but has other issues around suspend, that is why I have updated the driver to the latest Nvidia.
Changing the rendering backend has helped. Thanks a lot frank770504!

---

