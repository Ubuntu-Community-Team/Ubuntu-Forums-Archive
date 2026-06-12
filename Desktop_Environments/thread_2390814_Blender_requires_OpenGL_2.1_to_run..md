---
title: "Blender requires OpenGL 2.1 to run."
date: 2018-05-02
forum: Desktop Environments
---

### Post by techagogical on 2018-05-02
Ive a fresh install of Ubuntu 18.04, and Blender reports the following when run from terminal:

```
Error! Blender requires OpenGL 2.1 to run. Try updating your drivers.
```

Ive installed mesa-utils but to no avail as far as Blender in concerned:

```

glxinfo | grep -i opengl
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Q35 
OpenGL version string: 1.4 Mesa 18.2.0-devel
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 18.2.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
```

Can anyone help?

---

### Post by monkeybrain20122 on 2018-05-03
The Q35 is more than 10 years old and is no longer supported by  Intel [https://www.intel.com/content/www/us/en/support/products/81513/graphics-drivers/legacy-graphics/graphics-drivers-for-intel-q35-express-chipset.html](https://www.intel.com/content/www/us/en/support/products/81513/graphics-drivers/legacy-graphics/graphics-drivers-for-intel-q35-express-chipset.html) 

It seems that OpenGL 1.4 is as good as you can get [https://en.wikipedia.org/wiki/Intel_GMA#GMA_3100](https://en.wikipedia.org/wiki/Intel_GMA#GMA_3100)

You need to upgrade your hardware apparently.

---

### Post by techagogical on 2018-05-03
Thank you for your reply.

Under 14.04 blender ran fine, I can't upgrade, its onboard...

---

### Post by &amp;KyT$0P# on 2018-05-03
> **techagogical said:**
> Under 14.04 blender ran fine, I can't upgrade, 
14.04 had [Blender version 2.69]("https://packages.ubuntu.com/trusty/blender").  If you download Blender 2.69 from [here]("https://download.blender.org/release/Blender2.69/"), does that work in your 18.04?

---

### Post by kostkon on 2018-05-03
You could try the following:
```
MESA_GL_VERSION_OVERRIDE=2.1 blender
```
If Blender starts and runs properly after that and you are satisfied with the results, you could then update its desktop file accordingly.

---

