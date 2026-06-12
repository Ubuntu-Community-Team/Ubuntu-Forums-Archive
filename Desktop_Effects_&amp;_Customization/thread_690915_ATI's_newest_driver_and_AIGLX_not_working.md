---
title: "ATI's newest driver and AIGLX not working?"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by rekahsoft on 2008-02-07
Hi all, i just installed the new ATI driver (8.01) and have got it working:```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7276 Release
```but when i run compiz --replace i get:```
compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
```I noted especially that it says that texture_from_pixmap is missing but acording to glxinfo it is now :'(:```
glxinfo | grep texture_from_pixmap
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
```...What is happening? is there a fix so i can get AIGLX/compiz up and running?

---

### Post by json25 on 2008-02-07
Thats exactly my setup and problem too!  Not sure the ATI Wiki is correct, I followed everything it said.  I've never gotten Compiz to work on anything though.

---

### Post by BloodThirstyEmu on 2008-02-08
i just did the fglrxinfo command and I get this :
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.0.6473 (8.37.6)

Is that the newest version of the ATI Drivers?

---

### Post by json25 on 2008-02-08
I get the same thing, so I think it is, I updated and downloaded it with apt-get yesterday.

---

