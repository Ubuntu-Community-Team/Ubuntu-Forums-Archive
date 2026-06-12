---
title: "Xgl and GLX displays"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by deavik on 2007-05-17
Hello everyone,

I installed Xgl+beryl on my ATI Xpress 200M laptop, and got it to work after some hiccups :).

But, it seems the default display is not getting direct rendering for some reason, but display 0.0 is working as it should:

```
$ glxinfo
name of display: localhost:1.0
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: localhost:1  screen: 0
direct rendering: No

$ glxinfo -display :0.0
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)
```

This is clearly shown by running glxgears, almost chokes on the default display but runs nicely on 0.0. I was wondering why this is happening ... if I write an opengl app i would want it to run in the default display with acceleration, and I was thinking, Xgl+beryl would benefit from acceleration too, wouldn't it? Is there any way to accelerate display 1.0 or make 0.0 the default?

Thanks!

---

