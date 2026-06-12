---
title: "XGL gives gives me a XFree86-SEI"
date: 2006-12-22
forum: Desktop Environments
---

### Post by b0le on 2006-12-22
When i login using XGL I get this error:

```
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

```
$ fglrxinfo -display  :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 1.2 (2.0.6011 (8.28.8))
```

However, when I login using a GNOME session, I get this:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

I have Ubuntu Edgy x64 installed with ATi proprietary drivers (8.32.5)

I am trying to get Beryl to work (which it won't - and I'm assuming this is because XGL isn't working properly)

Help please,

Thanks, Joel

EDIT: Also, does anyone know how to make the time stay changed (I change it and then after a while it changes back - I have disabled updating with time server aswell?)

---

### Post by b0le on 2006-12-22
When trying to start beryl from the terminal (when I am using an XGL session) I get this error:

```

XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```

---

