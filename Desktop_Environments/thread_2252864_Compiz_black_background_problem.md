---
title: "Compiz black background problem"
date: 2014-11-15
forum: Desktop Environments
---

### Post by luis45 on 2014-11-15
(also posted in [askubuntu.com]("http://askubuntu.com/questions/549914/compiz-black-background-problem/549926#549926"))

After a reboot suddently Compiz stopped showing the background and when I drag windows along it I get the following effect:

  [http://i.stack.imgur.com/98LUN.png](http://i.stack.imgur.com/98LUN.png) (note at the left that the files on the desktop stand on the foreground)

If I go to the settings and disable OpenGL it stops doing this but  that's not a solution. 

Already tried resetting settings (rm -rf  ~/.config/compiz-1/compizconfig/*) and uninstalling (with apt-get purge)  compiz but it didn't help out.


  Wtf happened and how can I fix it?

---

### Post by grahammechanical on 2014-11-15
My guess is that your system is right now running on the Ubuntu open source fall back video driver. It is called llvmpipe. The Details page confirm that. We get llvmpipe when

a) We install Ubuntu and the graphic adapter cannot do hardware accelerated 3D rendering and all 3D rendering has to be done by the CPU.
b) We select Recovery mode Resume.
c) There is some problem with a proprietary video driver.

Try experimenting with different video drivers in Software and Updates>Additional Drivers tab.

Regards.

---

### Post by CantankRus on 2014-11-15
To confirm your gfx driver, run...
```
/usr/lib/nux/unity_support_test -p 
```

eg
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **/usr/lib/nux/unity_support_test -p **
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.38

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

---

