---
title: "desktop effects annot be enabled?"
date: 2009-06-05
forum: General Help
---

### Post by abhilashm86 on 2009-06-05
i've compiz on my ubuntu 8.04, i'm not able to enable effects, what is the reason, how can i recover?
when i go to apperance menu ,then visual effects then click extra,this is happening, pls help, i'm missing my dock n cube n shift swicher :(

---

### Post by overdrank on 2009-06-05
> **abhilashm86 said:**
> i've compiz on my ubuntu 8.04, i'm not able to enable effects, what is the reason, how can i recover?
when i go to apperance menu ,then visual effects then click extra,this is happening, pls help, i'm missing my dock n cube n shift swicher :(

Hi and what is the model of the graphics card and are the drivers installed?
You may use this command in the terminal ```
lspci | grep VGA
``` to identify your graphics.
You may also look at the FAQ's link in my signature.

---

### Post by abhilashm86 on 2009-06-05
> **overdrank said:**
> Hi and what is the model of the graphics card and are the drivers installed?
You may use this command in the terminal ```
lspci | grep VGA
``` to identify your graphics.
You may also look at the FAQ's link in my signature.

yes the graphics card is enabled, its Nvidia 
```
abhilash@abhilash:~$ lspci | grep VGA
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7050/nForce 610i (rev a2)


```

---

### Post by abhilashm86 on 2009-06-05
in system->admistration, propriety driver has been downloaded and installed,
this is shown in hardware drivers

---

### Post by overdrank on 2009-06-05
> **abhilashm86 said:**
> in system->admistration, propriety driver has been downloaded and installed,
this is shown in hardware drivers

Ok you may try [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by abhilashm86 on 2009-06-05
> **overdrank said:**
> Ok you may try [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070")

this script is just awesome, i got my compiz back:)
i guess you wanna see what it did,
[PHP]abhilash@abhilash:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 7050/nForce 610i (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Another compositing manager in use. 

Would you like to know more? (Y/n) y

 The default window manager of GNOME has its own compositing manager to
 provide basic desktop effects.
 If this one is in use, Compiz will not be able to run. 

Do you want to disable GNOME's compositing manager? (Y/n) y
abhilash@abhilash:~$ Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
[/PHP]

thanku overdrank :)

---

