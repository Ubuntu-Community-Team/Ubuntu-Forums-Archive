---
title: "Unity over Xubuntu"
date: 2012-01-03
forum: Desktop Environments
---

### Post by subehsharma on 2012-01-03
I have Xubuntu 11.10. Today i installed 'ubuntu-desktop' package to install Unity graphical environment. Unity 2d is working fine but 3d is not. When i log in, i could hear the Ubuntu login sound and then the wallpaper loads for few seconds and then a black screen is shown. I could see still my mouse pointer though. Any ideas?

---

### Post by grahammechanical on 2012-01-03
You do not give any information about the hardware in your machine. Let us find out if you have a video card that can run Unity 3D. Put this command in a terminal:

```
/usr/lib/nux/unity_support_test -p
```

You need to see something like this:


> Not software rendered:    yes
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

Another thing, Ubuntu 3D uses something called Compiz as the window or compositing manager. Ubuntu 2D uses Metacity. Xubuntu uses Xfce . You may have installed the Ubuntu-desktop package but did it include Compiz? Open the Software Centre and search for Compiz and confirm that Compiz is installed.

Regards.

---

### Post by subehsharma on 2012-01-03
Thanks. I've resolved it myself. I went to CCSM(while in UNity 2d) and 'enabled' Unity plugin. After that I logged out and log into Unity 3d. This time it worked! :-)

---

