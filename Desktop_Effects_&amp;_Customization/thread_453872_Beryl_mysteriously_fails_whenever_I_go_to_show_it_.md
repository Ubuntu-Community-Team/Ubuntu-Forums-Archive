---
title: "Beryl mysteriously fails whenever I go to show it off..."
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by WaeV on 2007-05-24
Yes beryl has failed on me again...  just as I am about to show it off.

When I go to select beryl as the window decorator it switches from my default 3 desktops to the four-in-one that make up the sides of the cube but immediately switches back.

```

beryl
```
output:
```
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /home/chad/flake.png
beryl: symbol lookup error: /usr/lib/beryl/libbench.so: undefined symbol: benchGetOutput_console
```

I have an ATI All-in-Wonder 9800 Pro and installed beryl using the mesa drivers and AIGLX.

I have tried reloading the window decorator and selecting beryl as the window decorator.
Both Cube Desktop and Rotate Cube are checked.

I know I'm overlooking something stupid.

---

### Post by ahaurw01 on 2007-05-27
Maybe try unchecking "launch fallback wm if beryl crashes" ?
(in right click menu on beryl icon)

---

