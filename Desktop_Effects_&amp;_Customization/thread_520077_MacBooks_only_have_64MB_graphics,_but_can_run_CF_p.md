---
title: "MacBooks only have 64MB graphics, but can run CF perfectly? I don't get it"
date: 2007-08-07
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-08-07
In the latest issue of Full Circle there was a comparison between the MacBook and some other laptop in terms of how good it is with Ubuntu, and in general. It said "the MacBook is probably the best system around at the moment if you want to run Ubuntu on a laptop. It is quiet and never overheats, it is powerful and eyecandy effects such as Beryl or Compiz Fusion will work perfectly with no slow down at all in any situation."
Sure, openGL is great, but 64MB?! I find it hard to believe that CF would be able to run perfectly "without any slow down in any situation", when it already runs kind of slow on my current Inspiron 8600 (which I KNOW has more than 64MB).
[http://www.apple.com/macbook/specs.html](http://www.apple.com/macbook/specs.html)
Can anyone clear this up for me?

---

### Post by dougfractal on 2007-08-07
> **rainwalker said:**
> In the latest issue of Full Circle there was a comparison between the MacBook and some other laptop in terms of how good it is with Ubuntu, and in general. It said "the MacBook is probably the best system around at the moment if you want to run Ubuntu on a laptop. It is quiet and never overheats, it is powerful and eyecandy effects such as Beryl or Compiz Fusion will work perfectly with no slow down at all in any situation."
Sure, openGL is great, but 64MB?! I find it hard to believe that CF would be able to run perfectly "without any slow down in any situation", when it already runs kind of slow on my current Inspiron 8600 (which I KNOW has more than 64MB).
[http://www.apple.com/macbook/specs.html](http://www.apple.com/macbook/specs.html)
Can anyone clear this up for me?

CF can run on 16MB all be it 16bit depth.

glxgears which should give you around 1300-1400 FPS.

---

### Post by rainwalker on 2007-08-07
> glxgears which should give you around 1300-1400 FPS.

...what are you talking about?

---

### Post by dougfractal on 2007-08-08
CF = compiz fusion ?


> **rainwalker said:**
> ...what are you talking about?
THe dell Inspiron 8600 has an ATi Radeon Mobility 9600 graphics card with 128MB which is capable of around 1300-1400 FPS in glxgears. This should give smooth CF.

I thought if it wasn't smooth you might like some help?

[http://www.trustedreviews.com/notebooks/review/2003/12/27/Dell-Inspiron-8600/p1](http://www.trustedreviews.com/notebooks/review/2003/12/27/Dell-Inspiron-8600/p1)
[http://www.student.dtu.dk/~s971652/ati_radeon.shtml](http://www.student.dtu.dk/~s971652/ati_radeon.shtml)

---

### Post by hyperair on 2007-08-08
Pffft. My system has 64MB of dedicated video memory, and CF runs fine, so there! I'm using nVidia Geforce 4 MX 440 AGP 8x (10de:0181). 

Please remember that memory is not all there is to determining the speed that Compiz Fusion runs. If your GPU is fast but has low memory it'll run faster than a GPU with loads of memory running slowly.

Misconfiguration can also lead to CF running slowly.

---

### Post by rainwalker on 2007-08-08
Ohh yeahh, that's a good point...I hadn't really thought of that

---

### Post by rainwalker on 2007-08-09
> **dougfractal said:**
> CF = compiz fusion ?



THe dell Inspiron 8600 has an ATi Radeon Mobility 9600 graphics card with 128MB which is capable of around 1300-1400 FPS in glxgears. This should give smooth CF.

I thought if it wasn't smooth you might like some help?

[http://www.trustedreviews.com/notebooks/review/2003/12/27/Dell-Inspiron-8600/p1](http://www.trustedreviews.com/notebooks/review/2003/12/27/Dell-Inspiron-8600/p1)
[http://www.student.dtu.dk/~s971652/ati_radeon.shtml](http://www.student.dtu.dk/~s971652/ati_radeon.shtml)

Okay, but what is glxgears? Is it that plugin thing that makes those gears in the middle of the 3D cube?

---

### Post by dougfractal on 2007-08-09
> **rainwalker said:**
> Okay, but what is glxgears? Is it that plugin thing that makes those gears in the middle of the 3D cube?

kind of.
wikipedea
> GLX (initialism for "OpenGL Extension to the X Window System") provides the 'glue' connecting OpenGL and the X Window System: it enables programs wishing to use OpenGL to do so within a window provided by the X Window System
glxgears was like one of the first apps to use GLX and demonstrate OGL in linux.
It also became an xscreensaver
as OGL advanced: glxgears > gears in the middle of the 3D cube
and altantis   > aquarium  in the middle of the 3D cube

But many people use glxgears (also fgl_glxgears for fglxr ) as a very basic benchmark

```
glxgears
```
leave for 10 secs.

---

