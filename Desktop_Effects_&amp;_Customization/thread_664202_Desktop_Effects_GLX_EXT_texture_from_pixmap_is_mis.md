---
title: "Desktop Effects: GLX_EXT_texture_from_pixmap is missing"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by DavyDuke17 on 2008-01-10
I am running an ATI Radeon Xpress 200m graphics card on Hardy with the 7.11 fglrx (8.42.3) driver. The driver appears to be working correctly, and glxinfo outputs the following:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
...
```

It says it has direct rendering, aiglx is working, and GLX_EXT_texture_from_pixmap, but yet when I try to run desktop effects it fails and says it can not be enabled. When I run SKIP_CHECKS="yes" compiz from the command line I get the following error:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

Thanks for the help.

---

### Post by hotgly on 2008-01-11
I've exactly the same problem with Hardy. And I also use ati catalyst 7.11.I've mobility raedon 9700, all works well except compiz.
Compiz-fusion worked well with gusty+fglrx but crashed after I upgrade to hardy.
No idea it's due to ati driver or to compiz.

---

### Post by family on 2008-01-12
I have the exact same problem on Gutsy. Except I have an i810 rev3.
This means that there isn't driver trouble, seeing as it is a problem with me too.
grr.
Please help?

---

