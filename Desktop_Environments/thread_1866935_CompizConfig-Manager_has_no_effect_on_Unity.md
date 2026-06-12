---
title: "CompizConfig-Manager has no effect on Unity"
date: 2011-10-22
forum: Desktop Environments
---

### Post by frozenthrone on 2011-10-22
Hello everybody,

Im am running Ubuntu 11.10 with Unity 3d. Or at least I think so because I've chosen "Ubuntu 3D" in the properties at the login screen.

One thing which is totally enerving is the very, very slow dash. It takes at least 4 seconds to open it! I've heard that it should be caused by a blur effect, which I tried to deactivate via CompizConfig Manager. But it seems that CCM does not effect on anything - not on the windows, nor on the dash.

Can you help me?

---

### Post by lovinglinux on 2011-10-22
Your system is probably falling back to 2D. Look at the top panel and check if it has a shadow below it. If not, then is 2D.

Make sure you have the latest driver for your video card installed. You can do that through *Additional Drivers* application.

---

### Post by frozenthrone on 2011-10-23
This is a screenshot of my front panel:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=205223&stc=1&d=1319364112[/IMG]

Seems like it wasn't throwing a shadow.

So if my computer is really falling back into 2D mode, what else can iI do to accelerate my dash? I have the latest nVidia driver installed.

---

### Post by 3Miro on 2011-10-23
When I adjust Unity with CCSM, sometimes I have to log-out log-in before the changes take place.

Having said that, what video card do you have? Older Nvidia models don't work with Unity regardless of the driver.

---

### Post by JRV on 2011-10-23
This command will tell you if your hardware will support Unity 3D:

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by frozenthrone on 2011-10-23
```
~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce4 Ti 4200 with AGP8X/PCI/SSE2
OpenGL version string:  1.5.8 NVIDIA 96.43.20

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    no
GL version is 1.4+:       yes

Unity 3D supported:       no

```Indeed, my hardware is slightly old. But is there no way to make a Unity a bit faster by switching off all useless effects?

---

### Post by Z80A on 2011-10-24
Have the very same issue; very slow Unity dash on Unity 2D. Tried to fix the blur thing using gconf-editor and this key:[INDENT] **/apps/compiz-1/plugins/unityshell/screen0/options/dash_blur_experimental**
[/INDENT]Changed the value from 2 to 0 to disable blur, but could not see any effect. Really need to speed up the dash - any ideas?

By the way; activating window shadows (as in Unity 3D) can be done with this key - no slow down and looks nicer:[INDENT] **/apps/metacity/general/compositor_effects**[/INDENT]

---

