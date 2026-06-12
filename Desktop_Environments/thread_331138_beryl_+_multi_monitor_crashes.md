---
title: "beryl + multi monitor crashes"
date: 2007-01-04
forum: Desktop Environments
---

### Post by rcasha on 2007-01-04
I have successfully set up beryl on my laptop (intel 915GM) - but only with one monitor. If I try to load beryl with the second screen in my xorg.conf, it crashes X11 something bad (blank screen, no keyboard response, not even Alt-Ctrl-F1/Backspace/Del) and I have to hard-reset the laptop. I'm using edgy (beryl-0.1.4~0beryl1 and xorg-7.1.1ubuntu6.2).

Any suggestions anyone? It feels like I'm so near and yet so far.

---

### Post by rcasha on 2007-01-08
ideas anyone?

---

### Post by quartzy on 2007-01-08
I know my brother had alot of problems with beryl and two monitors, having them in a xinerama sort of config doesn't work for sure - also there is a limit on the max resolution size and it considers both the screens resolutions into that.

Get the monitor working without beryl first? (if you havent already)

---

### Post by rcasha on 2007-01-08
Yes, dual monitor works without beryl. It's only when I actually launch beryl (or beryl-manager) that X crashes. The resolution is reasonably high (laptop=1024x768 + crt=1280x1024) but it shouldn't crash if the resolution is too high should it?

---

### Post by quartzy on 2007-01-08
I don't know then sorry :(

EDIT: Does two monitors work without beryl?

---

### Post by orb9220 on 2007-01-08
Check in the beryl forums [http://www.beryl-project.org/features.php](http://www.beryl-project.org/features.php)  I think I saw your problem
there somewhere.

Has to do with xinerama I think.

I have nvidia using two monitors works fine but has a couple of it's own bugs with no fixes yet.

Good luck

---

### Post by rcasha on 2007-01-08
couldn't find it there. incidentally i tried both with and without xinerama extensions in the xorg.conf (ie, serverlayout with 2 screens but no xinerama) but X still crashed.

---

### Post by Triskal on 2007-09-11
Did you get this problem solved?  I would like to do the same, but haven't found a solution.

---

### Post by rcasha on 2007-09-11
Sorry, no.

---

### Post by tenjin1 on 2007-09-17
I am using Dual monitors with Beryl as well. CRT+TV out. When I first installed Beryl it was workign fine (on CRT monitor not TV). But I started it up today and keeps falling back to gnome.

I get this when running from termail:
```
tenjin@Ubuntu:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Checking Screen 1 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

2 screens detected.
Currently we cannot guarantee that Beryl will work correctly with multiple X screens.
Using the --no-context-share command line option can help.
Please report any success to the beryl developer mailing list. The list can be found at lists.beryl-project.org
Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Checking Screen 1 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

2 screens detected.
Currently we cannot guarantee that Beryl will work correctly with multiple X screens.
Using the --no-context-share command line option can help.
Please report any success to the beryl developer mailing list. The list can be found at lists.beryl-project.org
Reloading options
beryl: glXCreateContext failed
beryl: Failed to manage screen: 1
Not a JPEG file: starts with 0x89 0x50

```

I am using Twinview with 2 seperate displays.

Any help would be appreciated.

---

### Post by tenjin1 on 2007-09-18
I removed Beryl and installed Compiz Fusion and dual monitors works fine right out of installation. I am happy with it, installed using this [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")

---

