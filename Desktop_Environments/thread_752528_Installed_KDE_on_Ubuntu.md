---
title: "Installed KDE on Ubuntu"
date: 2008-04-11
forum: Desktop Environments
---

### Post by 34.50 on 2008-04-11
I have Ubuntu installed (Gnome) and decided I wanted to install the KDE desktop environment. I can login to KDE just fine. It doesn't feel like the video is hardware accelerated. I have an ATI x200M integrated video card. 

Under System Settings -> Monitor & Display -> Hardware tab, it says its using fglrx driver, but I somehow doubt it. I tried clicking the Administrator Mode, but it doesn't let me change anything. I checked the Restricted Drivers and it says ATI accelerated graphics is in use...:confused: The video transitions are choppy, and it doesn't feel accelerated. 

Does anyone know how I can install/enable the correct drivers to accelerate video?

Thanks in advance. :)

---

### Post by warp99 on 2008-04-11
Run this:

```
lsmod |grep fglrx
```

If listed they're loaded. Also check to see if direct rendering is enabled:

```
glxinfo | grep render
```

---

### Post by 34.50 on 2008-04-11
Here is the output:

root@kUbuntu:/home/ku# lsmod |grep fglrx
fglrx                 656352  27 
agpgart                35016  2 fglrx,ati_agp

root@kUbuntu:/home/ku# glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Radeon Xpress Series

Thanks for your reply. What do I do from here?

---

### Post by warp99 on 2008-04-11
You are missing direct rendering so try the following:

```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) xorg-driver-fglrx
```

Then reboot. Check to make sure direct rendering is working:

```
glxinfo | grep render
```

and the drivers are in use:

```
fglrxinfo
```

if you want to change you monitor settings use the ati control panel. If not listed in the menu then install it:

```
sudo apt-get install fglrx-control
```

Edit:

If you run into any problems use this guide for troubleshooting:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by 34.50 on 2008-04-11
Well after executing the first command and rebooting, I can't change sessions... Help?

Edit : Nevermind, got it to select somehow... Ran the other commands, here's the output:

ku@kUbuntu:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Radeon Xpress Series

ku@kUbuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

Seems a little bit better, but anyway to turn off any fancy effects to make the transitions smoother?

---

### Post by warp99 on 2008-04-11
It looks like the fglrx drivers are not enabled so try the following:

```
sudo dpkg-reconfigure xserver-xorg
```

choose fglrx as the driver, then when you reach the monitor section choose your resolution and any resolution **above** your resolution remove from the list. Then crtl+alt+backspace to reload xserver. You may have to reboot, but most likely no.

---

### Post by 34.50 on 2008-04-11
I tried to do what you said, with the exception of the resolution part. Nothing was selected, so I just selected my native and accepted all the default values of the installation thereafter. 

When I ran the commands, I got the same result. Oh well, I don't know what to do. I guess I give up. Here is the output of the commands...


ku@kUbuntu:~$ glxinfo | grep render
Xlib: extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Radeon Xpress Series

ku@kUbuntu:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

I appreciate all your help. Thank you very much. :)

---

### Post by warp99 on 2008-04-11
Please do the following:

```
cat /etc/X11/xorg.conf
```

and post the results to this thread. Also what resolution do you want your monitor to run. 800x600? 1024x768? or higher? Please let me know.

---

