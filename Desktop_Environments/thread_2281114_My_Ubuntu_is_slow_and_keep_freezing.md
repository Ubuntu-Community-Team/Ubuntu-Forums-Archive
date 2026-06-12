---
title: "My Ubuntu is slow and keep freezing"
date: 2015-06-04
forum: Desktop Environments
---

### Post by moktar2 on 2015-06-04
CPU Intel® Core™2 Duo CPU E6550 @ 2.33GHz × 2 
Memory 2GB
Graphic Intel® Q35 x86/MMX/SSE2
OS 32-bit


I think Unity is the reason for this freezing, I need a light interface 
can anyone help please?

---

### Post by tgalati4 on 2015-06-04
Open a terminal and post the output of:

```
free
```

2 GB may not be enough with firefox or chrome and a lot of tabs open.  The freezing could simply be a lot of swap activity.

---

### Post by moktar2 on 2015-06-04
Thanks for responding



```
free             total       used       free     shared    buffers     cached
Mem:       2054304    1709504     344800     203776      45660     736508
-/+ buffers/cache:     927336    1126968
Swap:      5346300     147148    5199152



```

---

### Post by moktar2 on 2015-06-04
I read about Unity needs a decent memory and graphic card
I also read that there are simpler interfaces 
how can I install simple interface if that is right

---

### Post by grahammechanical on 2015-06-04
In my opinion every user interface is both simple and complex at the same time.

The CPU in that machine is powerful enough to run Ubuntu Unity 3D and the mount of RAM is more than enough. I am getting by with half that amount of RAM. You need to look at the graphic adapter. It is integrated graphics. How much of it own memory does it have?

[http://ark.intel.com/products/31918/Intel-82Q35-Graphics-and-Memory-Controller#@specifications](http://ark.intel.com/products/31918/Intel-82Q35-Graphics-and-Memory-Controller#@specifications)

To see if it can run Unity 3D run this command

```
usr/lib/nux/unity_support_test -p
```

You do not say what version of Ubuntu you are using but if you do not want to re-install with Xubuntu or Lubuntu then search the software centre for gnome session flashback (gnome-session-flashback).

It has a different user interface to Unity but it gives us 2 extra login options: Gnome Flashback (Compiz) & Gnome Flashback (Metacity). It is the Metacity session that will give a "lighter" desktop compositor.

Regards.

---

### Post by moktar2 on 2015-06-04
Thanks for respond 
after what you said i think I'll stick to Ubuntu 
I'm using Ubuntu 14.04 LTS 32bit


```
/usr/lib/nux/unity_support_test -pOpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Q35 x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 10.3.2


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

### Post by houstonbofh on 2015-06-04
I have been running Ubuntu Mate, and it is still full featured, but a lot leaner than Unity.  Give it a try.

---

