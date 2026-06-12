---
title: "window dragging eats all cpu"
date: 2005-10-26
forum: Desktop Environments
---

### Post by wrynn on 2005-10-26
why is window dragging so sloww and eating all my cpu?  is this a configuration problem with gnome?  i have the nvidia-drivers installed

---

### Post by Dr. Nick on 2005-10-27
[QUOTE=wrynn]why is window dragging so sloww and eating all my cpu?  is this a configuration problem with gnome?  i have the nvidia-drivers installed[/QUOTE]

Not sure how much it matters but have you added render acel to your xorg.conf?

```
Section "Device"
        Identifier      "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection
```

You can disregard the allowglxwithcomposite if you dont know what it means, try to put the ```
Option          "RenderAccel"           "true"
``` in your xorg.conf file though and make sure the driver is on nvidia. My cpu incereases on window move , but not to 100% and I dont get a obvious slowdown

---

### Post by wrynn on 2005-10-28
AllowGLXWithComposite requires that i have composite x installed right?

---

### Post by Dr. Nick on 2005-10-28
[QUOTE=wrynn]AllowGLXWithComposite requires that i have composite x installed right?[/QUOTE]


If you put it in their and dont have a composite manager it just wont do anything, But if you ever want to use a compostire manager you will need it. 

You do not need a special version of X installed for it to work, its just needed for some composite applications to work

---

### Post by rwabel on 2005-11-03
I do have "RenderAccel" set to "true" but dragging a window still eats up all my cpu ressource. That's very strange.

---

