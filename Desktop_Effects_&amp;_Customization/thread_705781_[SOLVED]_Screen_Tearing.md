---
title: "[SOLVED] Screen Tearing"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by Bionic Apple on 2008-02-23
I have been looking around to solve my screen tearing problem, but to no avail.  There is screen tearing when I use Compiz effects, when I move windows, watch movies, and more.  I have configured my Xorg server using the one command and using Envy.  All 3 of the Vsync to Blank settings have been enabled in Nvidia Settings.  I have a 7900GT (which may be the problem) with the 169.09 driver.  Any help?  Also, it may be related with this: [http://ubuntuforums.org/showthread.php?t=671279](http://ubuntuforums.org/showthread.php?t=671279)

Also, is it bad that my GPU's fan is running at full power when there are no drivers?  I assumed it wasn't because it is factory overclocked.

---

### Post by Bionic Apple on 2008-02-24
Bump, I can't find another thread that solves this problem.

---

### Post by ahaslam on 2008-02-24
Try:
```
nvidia-settings -a OpenGLImageSettings=3 -a SyncToVBlank=1
```
That'll optimize opengl performance & enable vsync. 

Your fan shouldn't be at full speed on the desktop though...

---

### Post by Bionic Apple on 2008-02-24
It only does that when there are no drivers, like when I use a Live CD or am in GRUB.  I will check if that command works in a sec...

[B]Update:
[/B]
That didn't work.  Another possible solution?

---

### Post by ahaslam on 2008-02-24
If you're using vesa, tearing is to be expected, as it's not accelerated...

---

### Post by FuturePilot on 2008-02-24
Open CompizConfig and in the General Section click on the Display Settings tab, and check the box for SyncToVblank. I'm not sure why the SyncToVblank in the nvidia-settings has no effect on Compiz.

---

### Post by Bionic Apple on 2008-02-25
> **FuturePilot said:**
> Open CompizConfig and in the General Section click on the Display Settings tab, and check the box for SyncToVblank. I'm not sure why the SyncToVblank in the nvidia-settings has no effect on Compiz.

That did it!  Thanks, that really is the type of answer I was looking for, also it was kind of obvious *facepalm*. They should really make the SyncToVblank in Compiz overridden by the GPU drivers, if they are present.

---

### Post by loldawson on 2008-04-04
This works great thanks :)

---

### Post by engelsen on 2008-04-13
Fantastic! This works great, solved my problem also. Thanks!

7900 GT, twinview, dual screens 1680x1050.

---

