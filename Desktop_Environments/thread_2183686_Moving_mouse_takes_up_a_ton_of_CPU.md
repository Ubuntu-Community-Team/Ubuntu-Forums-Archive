---
title: "Moving mouse takes up a ton of CPU"
date: 2013-10-25
forum: Desktop Environments
---

### Post by Xorlium on 2013-10-25
Hello,

I installed kubuntu 13.10 a few days ago. My laptop has always had the problem that it gets hot too quickly, but now it's ridiculous. I press CTRL-ESC to see how much CPU each program is using. If I stop everything, then lightdm or kdm (tried with both) go to 2-7%. But if I start moving the mouse (yes, just moving it around), it jumps up to 20-50%, and the laptop gets hot!! Moving windows, interacting, etc, has the same effect of making my cpu usage jump, but for example, not writing this post without moving the mouse. The faster I move the mouse, the higher it jumps. I didn't know you needed a 2.6Ghz processor to handle mouse input...

Also, moving the mouse wheel, even when not pointed at anything. Both with an external mouse and with the square thingy that moves the mouse in the laptop.

I tried disabling desktop effects and it's the same. I'm not really sure what to do now or where to ask. A google search reveals nothing.

Thank you!
Xorlium

---

### Post by Erik1984 on 2013-10-26
That's a weird problem. Do you have any custom mouse cursor theme in place? If I move the mouse (slow or fast) I see practically no increase in CPU usage at all. I guess it's the combo Kwin and your graphics drivers. Have you tried other DEs (Unity, Gnome, XFCE etc.) on the same machine to see if that makes any difference?

---

### Post by vasa1 on 2013-10-26
> **Euroman said:**
> That's a weird problem. Do you have any custom mouse cursor theme in place? If I move the mouse (slow or fast) I see practically no increase in CPU usage at all. I guess it's the combo Kwin and your graphics drivers. Have you tried other DEs (Unity, Gnome, XFCE etc.) on the same machine to see if that makes any difference?
I have a laptop without a **G**PU. For me, if I move the mouse about on this site, nothing much happens but if I do the same on [http://ubuntu-discourse.org/](http://ubuntu-discourse.org/) (lots of HTML5 ???), a rise in % CPU usage is clear. I can't tell how much but it is higher (~10% or so?).
So window content and whether one has a GPU *may* be relevant. OS = Lubuntu 13.10.

---

### Post by Xorlium on 2013-10-27
Hello,

Thank you for your replies. I've spent some time testing the things you guys suggested. I closed all other applications, except for CPU monitor, and it's the same. I installed unity (ugh), and it's the same. Moving the mouse just causes a CPU jump. I't higher when desktop effects are installed than when they aren't. I tried different mouse cursor themes, and there is no change.

I have no idea what could be going on...

According to the system monitor, the ones taking up CPU are: Xorg, kdm, init, plasma-desktop. Each one of those consistently jumps up when I start moving the mouse, and drops back down when I stop moving it.

Thanks.

---

### Post by oldos2er on 2013-10-27
You can try some of the optimizations [here]("http://ubuntuforums.org/showthread.php?t=1889034"), in particular the 'Low display resolution and Low CPU' setting in Application Appearance, Style. I don't know if it will help but it certainly won't hurt.

---

### Post by J_Me on 2013-10-27
On my intel atom netbook kubuntu was vertually unusable until I went into settings > configure desktop effects > advanced > opengl options > and unchecked use opengl 2 shaders. If that doesn't work try switching compositing type to xRender

---

### Post by Xorlium on 2013-10-27
Hi,

Thanks to both of your replies. I've tried both those things. Switching off desktop effects, as I said, has some minor improvement, but no solution. The Low Display-Low CPU was the first thing I tried, and I didn't notice any improvement whatsoever.

Thanks.

---

### Post by klaus6 on 2014-05-29
Hi, any updates on this? Have the same problem on Ubuntu 14.04 LTS (3.13.0-27) with fglrx (OpenGL version string: 4.3.12798 Compatibility Profile Context 13.35.1005) Moving the mouse let all 4 cores go to ~25% usage.

EDIT: After switching desktop effects to OpenGL version 2.0, usage has been decreased a little. Three cores go to ~10% and one ~20%. But I have the feeling, that this is still quite high usage.

---

### Post by fkkroundabout on 2014-05-29
are you in compatibilty mode ??

---

