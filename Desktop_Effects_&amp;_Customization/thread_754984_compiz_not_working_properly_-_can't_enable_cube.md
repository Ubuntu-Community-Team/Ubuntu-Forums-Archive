---
title: "compiz not working properly - can't enable cube"
date: 2008-04-14
forum: Desktop Effects &amp; Customization
---

### Post by gators38 on 2008-04-14
here's compiz terminal output:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c5 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

ubuntu 8.04 hardy
radeon x1600 mobile

---

### Post by Zorael on 2008-04-14
Elaborate, please. In what way doesn't it work? No titlebars/window borders, or does it simply do nothing? Or is it the case of the Desktop Cube plugin unchecking itself automatically, in CCSM? (package name **compizconfig-settings-manager**)


```
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
```
That suggests you don't have any window decorators installed, which is curious, since Compiz should come with gtk-window-decorator and kde-window-decorator. Regardless; do you have Emerald installed? (package name **emerald**)

---

### Post by gators38 on 2008-04-14
Sorry for not being more clear. Nothing happens when I enable all the cube options in "Advanced Desktop Settings". When I go to "Appearance" -> "Visual Effects" only the following exist:
None, Normal, Extra. I believe there used to be a "Custom" option?

---

### Post by Zorael on 2008-04-15
Install the **compizconfig-settings-manager** package via Synaptic. Once installed, it should pop up someplace in your Applications panel menu, but you can also start it by running **ccsm**, either from a terminal or from a run box (Alt+F2).

It's a bit more complicated than the Advanced Desktop Effects thingy (which is a dumbed down version), but try enabling Desktop Cube and Rotate Cube.

Remember that you want Number of Desktops set to 1 and Horizontal Virtual Desktops set to 4 under General Options.

---

### Post by gators38 on 2008-04-15
> **Zorael said:**
> Install the **compizconfig-settings-manager** package via Synaptic. Once installed, it should pop up someplace in your Applications panel menu, but you can also start it by running **ccsm**, either from a terminal or from a run box (Alt+F2).

It's a bit more complicated than the Advanced Desktop Effects thingy (which is a dumbed down version), but try enabling Desktop Cube and Rotate Cube.

Remember that you want Number of Desktops set to 1 and Horizontal Virtual Desktops set to 4 under General Options.

I'm not sure if it just needed a reinstall or if the # desktop settings were off, but it's working now!
Thank you for the help.

---

### Post by MedellinManDem on 2008-04-16
You don't just have to have a cube, you can have any shape. 

I have a hexagon.

---

### Post by Zorael on 2008-04-16
Certainly, but you can't have a dodecahedron. To be fair, the most common misstep is to set Number of Desktops to 4, since vertical virtual desktops didn't exist in Beryl.

And he asked for help to enable his **cube**.

---

### Post by MedellinManDem on 2008-04-16
Come on man, no need to be anal about it...

---

### Post by Zorael on 2008-04-16
Not my intention. :>

My apologies if I came through as aggressive.

---

