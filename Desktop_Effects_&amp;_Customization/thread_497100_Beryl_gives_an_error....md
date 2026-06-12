---
title: "Beryl gives an error..."
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by iDante on 2007-07-09
Well, I installed beryl a while ago and it worked fine until I restarted. Now, whenever I try to run beryl I get this:

```
beryl
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

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual

```

And when I run beryl-manager I get:

```
extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real: Root visual is not a GL visual
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


```

Any help would be nice, I would like to get this running again.

---

### Post by Waappu on 2007-07-09
Hi

You can try these solutions by modifying sections of /etc/X11/xorg.conf :


1. Try changing DefaultDepth to 24 in the ' Screen ' section.

2. Delete, if existing, these entries in ' Section "Module" ' :

 Load "dri"
 Load "GLCore"

3. Add this entry in ' Section "Module" ' :

 Load "glx"

4. Change in Section "Device" the ' Driver "nv" ' entry to :

 Driver "nvidia"

5. Add this entry in ' Section "Screen" ' :

 Option "AddARGBGLXVisuals" "True"

6. Add this section at the end of the file:

 Section "Extensions"
     Option "Composite" "Enable"
 EndSection

---

### Post by iDante on 2007-07-09
Most of those changes were already in it. I added the last bit but it still doesn't work.

---

