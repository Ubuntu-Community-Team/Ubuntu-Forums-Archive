---
title: "Graphical Login problem libGLCore error reoccurence"
date: 2006-09-05
forum: Desktop Environments
---

### Post by pt123 on 2006-09-05
Every second time (around about that) I boot up I get this error which screws  xserver like the major bug 2 weeks ago.

so when I checked the logs of when it crashed and when it didn't it is still giving me the same error in the log. 
```
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
```

in the log which loaded successfully:
```
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)
(II) LoadModule: "bitmap"
```

Is there a way to fix this](*,)

---

### Post by pgabriel on 2006-09-14
The problem with libGLcore is not an actual error.
The Xorg GLcore module in Dapper is part/sub_module of glx and is loaded by glx. It will load correctly if you load glx, you should see something like this in the logfile:```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
```
If you try to load it as a separate module you will get that error.

---

