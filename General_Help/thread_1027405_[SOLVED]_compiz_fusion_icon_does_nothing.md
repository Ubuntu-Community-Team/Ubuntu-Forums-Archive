---
title: "[SOLVED] compiz fusion icon does nothing"
date: 2009-01-01
forum: General Help
---

### Post by reahjw6 on 2009-01-01
Hey all
I have compiz installed and installed compiz icon but when i click on it it does nothing.
I am running 8.10.
Thanks reah.

---

### Post by gjoellee on 2009-01-01
Make sure to add compiz icon to startup. Find "Sessions" and add the compiz icon. (I am not usre about the command, but you can easy find it my hitting Alt+F2 and start writing what you need the command for).

Then next time you log in you will have the compiz icon in your systems notification area. Right click on the icon and you will find some options.

---

### Post by reahjw6 on 2009-01-01
thanks i have done that but when i right click and try to launch it does nothing at all.

---

### Post by reahjw6 on 2009-01-01
/home/reahjw6/Desktop/Screenshot.png
This is the reply when i run it in terminal

---

### Post by reahjw6 on 2009-01-01
* Detected Session: gnome
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface

---

### Post by stderr on 2009-01-01
I'm rather confused with what's going on... we're talking about 'fusion-icon'?

When installed, it adds a menu entry to Applications -> System Tools -> Compiz Fusion Icon. When you open that, or if you add the command fusion-icon to System -> Preferences -> Sessions and restart your WM, a blue icon gets placed in your system tray.

Do you get the blue icon?

Then, when you right-click on the icon, you should get a menu with

```
Settings Manager
Reload Window Manager
Select Window Manager
Compiz Options
Select Window Decorator
Quit
```

Do you get that?

If so, what is it failing to do?

---

### Post by reahjw6 on 2009-01-02
THanks for reply
I can get the blue icon and can put it in a panel or desktop but when i right click i get none of the above you listed is displayed only get the panel commands  launch properties remove from panel etc same as the commads in the system tray i only get those commands. when i right click on the icon i get none of the commands you have displayed.
It just does nothing.

---

### Post by ellalan on 2009-01-02
Click on that icon and you'll get another icon on the right side near your user name, network icons, then you have to right click that and you'll get the menu as the previous poster said.

---

### Post by reahjw6 on 2009-01-02
I have been doing that from day one but it opens nothing.
I get the icon but no menue.
I have tried to uninstall and reinstall but what ever i do it still does not bring up the icons menue.

---

### Post by Forlong on 2009-01-02
Make sure you actually have the tray on your gnome panel.
Right click the panel where you want it to be and choose add to panel then look for the notification area.

---

### Post by hyperdude111 on 2009-01-02
go to synaptic and install ALL apps relating to compiz, mainly compizconfic settings manager. Once you have done that right click on your desktop and select chose desktop background chose he visual effects tab and choose *extra*
It should enable sone effects then go system preferences compizconfig settings manager and chose wich preferneces you want.

---

### Post by reahjw6 on 2009-01-02
Thanks for reply
I installed compiz switch following your instructions after uninstalling the compiz icon i previously had now when i click on the icon i get screen not composited realy fed up with it know.
I ran compiz-check and all is ok.
When screen not composited comes up it knocks out awn and some effects from ccsm.
THANKS anyway REAH

---

### Post by reahjw6 on 2009-01-02
HEY HYPERDUDE Thanks for reply
Thats what i origannaly did its just the compiz icon does nothing when i right click.
Now i have another problem see above.
Reah

---

### Post by Forlong on 2009-01-02
**reahjw6**, are you certain you have a working notification area (system tray) on your panel?
That was my original question.

It sounds like you are trying to use the **launcher** for fusion-icon as the actual application.
Like many others were already trying to point out to you: **fusion-icon runs in the notification area**. **You can not move the icon** itself (unlike Compiz-Switch).
If you are able to move the icon around it is not the actual application but merely it's launcher.

The notification area is the part of your panel were the Network-Manager should be always visible. If you do not have the Network-Manager icon on your panel, that means you have no system tray.
Go to my previous post to find out how to get it back.

---

### Post by reahjw6 on 2009-01-02
Thanks i now am able to work the icon ok.
I now have the error screen not composited coming up.
When i enable compiz and have to enable extras again and reset the effects i want.
Reah

---

### Post by Forlong on 2009-01-03
What's the output of ```
compiz
``` in a terminal?

Also, post the full output of Compiz-Check here and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by reahjw6 on 2009-01-03
Forlong Firstly thanks for your time and patience it is greatly appreciated.
Here is the output from compiz

reahjw6@reahjw6-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x0a3016d0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7a9d3f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7a9f456]
/usr/lib/libGL.so.1[0xb7c050e1]
======= Memory map: ========
08048000-0807c000 r-xp 00000000 08:01 3408521    /usr/bin/compiz.real
0807c000-0807d000 r--p 00033000 08:01 3408521    /usr/bin/compiz.real
0807d000-0807e000 rw-p 00034000 08:01 3408521    /usr/bin/compiz.real
0990e000-0a472000 rw-p 0990e000 00:00 0          [heap]
b4fff000-b5006000 r--s 00000000 08:01 9429235    /usr/lib/gconv/gconv-modules.cache
b5006000-b5045000 r--p 00000000 08:01 3474499    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b6400000-b6421000 rw-p b6400000 00:00 0 
b6421000-b6500000 ---p b6421000 00:00 0 
b6529000-b6533000 r-xp 00000000 08:01 3343526    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6533000-b6534000 r--p 00009000 08:01 3343526    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6534000-b6535000 rw-p 0000a000 08:01 3343526    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6535000-b653e000 r-xp 00000000 08:01 3343530    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b653e000-b653f000 r--p 00008000 08:01 3343530    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b653f000-b6540000 rw-p 00009000 08:01 3343530    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6540000-b6547000 r-xp 00000000 08:01 3343522    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6547000-b6548000 r--p 00006000 08:01 3343522    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6548000-b6549000 rw-p 00007000 08:01 3343522    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6549000-b655e000 r-xp 00000000 08:01 3343520    /lib/tls/i686/cmov/libnsl-2.8.90.so
b655e000-b655f000 r--p 00014000 08:01 3343520    /lib/tls/i686/cmov/libnsl-2.8.90.so
b655f000-b6560000 rw-p 00015000 08:01 3343520    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6560000-b6562000 rw-p b6560000 00:00 0 
b6562000-b658a000 r-xp 00000000 08:01 3326065    /lib/libpcre.so.3.12.1
b658a000-b658b000 r--p 00027000 08:01 3326065    /lib/libpcre.so.3.12.1
b658b000-b658c000 rw-p 00028000 08:01 3326065    /lib/libpcre.so.3.12.1
b658c000-b65a1000 r-xp 00000000 08:01 3343535    /lib/tls/i686/cmov/libpthread-2.8.90.so
b65a1000-b65a2000 r--p 00014000 08:01 3343535    /lib/tls/i686/cmov/libpthread-2.8.90.so
b65a2000-b65a3000 rw-p 00015000 08:01 3343535    /lib/tls/i686/cmov/libpthread-2.8.90.so
b65a3000-b65a5000 rw-p b65a3000 00:00 0 
b65a5000-b65e1000 r-xp 00000000 08:01 3408572    /usr/lib/libgobject-2.0.so.0.1800.2
b65e1000-b65e2000 r--p 0003b000 08:01 3408572    /usr/lib/libgobject-2.0.so.0.1800.2
b65e2000-b65e3000 rw-p 0003c000 08:01 3408572    /usr/lib/libgobject-2.0.so.0.1800.2
b65e3000-b6619000 r-xp 00000000 08:01 3326004    /lib/libdbus-1.so.3.4.0
b6619000-b661a000 r--p 00035000 08:01 3326004    /lib/libdbus-1.so.3.4.0
b661a000-b661b000 rw-p 00036000 08:01 3326004    /lib/libdbus-1.so.3.4.0
b661b000-b6636000 r-xp 00000000 08:01 3410844    /usr/lib/libdbus-glib-1.so.2.1.0
b6636000-b6637000 r--p 0001a000 08:01 3410844    /usr/lib/libdbus-glib-1.so.2.1.0
b6637000-b6638000 rw-p 0001b000 08:01 3410844    /usr/lib/libdbus-glib-1.so.2.1.0
b6638000-b663f000 r-xp 00000000 08:01 3343539    /lib/tls/i686/cmov/librt-2.8.90.so
b663f000-b6640000 r--p 00007000 08:01 3343539    /lib/tls/i686/cmov/librt-2.8.90.so
b6640000-b6641000 rw-p 00008000 08:01 3343539    /lib/tls/i686/cmov/librt-2.8.90.so
b6641000-b6645000 r-xp 00000000 08:01 3408615    /usr/lib/libgthread-2.0.so.0.1800.2
b6645000-b6646000 r--p 00003000 08:01 3408615    /usr/lib/libgthread-2.0.so.0.1800.2
b6646000-b6647000 rw-p 00004000 08:01 3408615    /usr/lib/libgthread-2.0.so.0.1800.2
b6647000-b6690000 r-xp 00000000 08:01 3410343    /usr/lib/libORBit-2.so.0.1.0
b6690000-b6698000 r--p 00049000 08:01 3410343    /usr/lib/libORBit-2.so.0.1.0
b6698000-b669a000 rw-p 00051000 08:01 3410343    /usr/lib/libORBit-2.so.0.1.0
b669a000-b669d000 r-xp 00000000 08:01 3408495    /usr/lib/libgmodule-2.0.so.0.1800.2
b669d000-b669e000 r--p 00002000 08:01 3408495    /usr/lib/libgmodule-2.0.so.0.1800.2
b669e000-b669f000 rw-p 00003000 08:01 3408495    /usr/lib/libgmodule-2.0.so.0.1800.2
b669f000-b6754000 r-xp 00000000 08:01 3408494    /usr/lib/libglib-2.0.so.0.1800.2
b6754000-b6755000 r--p 000b4000 08:01 3408494    /usr/lib/libglib-2.0.so.0.1800.2
b6755000-b6756000 rw-p 000b5000 08:01 3408494    /usr/lib/libglib-2.0.so.0.1800.2
b6756000-b6784000 r-xp 00000000 08:01 3411022    /usr/lib/libgconf-2.so.4.1.5
b6784000-b6785000 ---p 0002e000 08:01 3411022    /usr/lib/libgconf-2.so.4.1.5
b6785000-b6786000 r--p 0002e000 08:01 3411022    /usr/lib/libgconf-2.so.4.1.5
b6786000-b6788000 rw-p 0002f000 08:01 3411022    /usr/lib/libgconf-2.so.4.1.5
b6788000-b679c000 r-xp 00000000 08:01 3408091    /usr/lib/libcompizconfig.so.0.0.0
b679c000-b679d000 r--p 00013000 08:01 3408091    /usr/lib/libcompizconfig.so.0.0.0
b679d000-b679e000 rw-p 00014000 08:01 3408091    /usr/lib/libcompizconfig.so.0.0.0
b67c1000-b69c1000 rw-s 32d72000 00:0e 16932      /dev/nvidia0
b6ac1000-b6ac2000 rw-s fac06000 00:0e 16932      /dev/nvidia0
b6bf1000-b6bfe000 r-xp 00000000 08:01 3326014    /lib/libgcc_s.so.1
b6bfe000-b6bff000 r--p 0000c000 08:01 3326014    /lib/libgcc_s.so.1
b6bff000-b6c00000 rw-p 0000d000 08:01 3326014    /lib/libgcc_s.so.1
b6c1c000-b6c52000 rw-p b6c1c000 00:00 0 
b6c52000-b6c74000 rw-s 00000000 00:09 0          /SYSV00000000 (deleted)
b6c74000-b6c75000 rw-p b6c74000 00:00 0 
b6c75000-b6c76000 r-xp 00000000 08:01 3597426    /usr/lib/tls/libnvidia-tls.so.177.82
b6c76000-b6c77000 rw-p 00000000 08:01 3597426    /usr/lib/tls/libnvidia-tls.so.177.82
b6c77000-b6c78000 rw-p b6c77000 00:00 0 
b6c78000-b7840000 r-xp 00000000 08:01 3408094    /usr/lib/libGLcore.so.177.82
b7840000-b79e4000 rwxp 00bc8000 08:01 3408094    /usr/lib/libGLcore.so.177.82
b79e4000-b79ef000 rwxp b79e4000 00:00 0 
b79ef000-b7a03000 r-xp 00000000 08:01 3412705    /usr/lib/libz.so.1.2.3.3
b7a03000-b7a05000 rw-p 00013000 08:01 3412705    /usr/lib/libz.so.1.2.3.3
b7a05000-b7a0d000 r-xp 00000000 08:01 3410558    /usr/lib/libXrender.so.1.3.0
b7a0d000-b7a0e000 r--p 00007000 08:01 3410558    /usr/lib/libXrender.so.1.3.0
b7a0e000-b7a0f000 rw-p 00008000 08:01 3410558    /usr/lib/libXrender.so.1.3.0
b7a0f000-b7a13000 r-xp 00000000 08:01 3410516    /usr/lib/libXdmcp.so.6.0.0
b7a13000-b7a14000 rw-p 00003000 08:01 3410516    /usr/lib/libXdmcp.so.6.0.0
b7a14000-b7a16000 r-xp 00000000 08:01 3410497    /usr/lib/libXau.so.6.0.0
b7a16000-b7a17000 rw-p 00001000 08:01 3410497    /usr/lib/libXau.so.6.0.0
b7a17000-b7a18000 rw-p b7a17000 00:00 0 
b7a18000-b7a19000 r-xp 00000000 08:01 3412670    /usr/lib/libxcb-xlib.so.0.0.0
b7a19000-b7a1a000 r--p 00000000 08:01 3412670    /usr/lib/libxcb-xlib.so.0.0.0
b7a1a000-b7a1b000 rw-p 00001000 08:01 3412670    /usr/lib/libxcb-xlib.so.0.0.0
b7a1b000-b7a28000 r-xp 00000000 08:01 3410522    /usr/lib/libXext.so.6.4.0
b7a28000-b7a2a000 rw-p 0000c000 08:01 3410522    /usr/lib/libXext.so.6.4.0
b7a2a000-b7a2c000 r-xp 00000000 08:01 3343515    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a2c000-b7a2d000 r--p 00001000 08:01 3343515    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a2d000-b7a2e000 rw-p 00002000 08:01 3343515    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a2e000-b7b86000 r-xp 00000000 08:01 3343509    /lib/tls/i686/cmov/libc-2.8.90.so
b7b86000-b7b88000 r--p 00158000 08:01 3343509    /lib/tls/i686/cmov/libc-2.8.90.so
b7b88000-b7b89000 rw-p 0015a000 08:01 3343509    /lib/tls/i686/cmov/libc-2.8.90.so
b7b89000-b7b8c000 rw-p b7b89000 00:00 0 
b7b8c000-b7bb0000 r-xp 00000000 08:01 3343517    /lib/tls/i686/cmov/libm-2.8.90.so
b7bb0000-b7bb1000 r--p 00023000 08:01 3343517    /lib/tls/i686/cmov/libm-2.8.90.so
b7bb1000-b7bb2000 rw-p 00024000 08:01 3343517    /lib/tls/i686/cmov/libm-2.8.90.so
b7bb2000-b7c39000 r-xp 00000000 08:01 3408090    /usr/lib/libGL.so.177.82
b7c39000-b7c53000 rwxp 00087000 08:01 3408090    /usr/lib/libGL.so.177.82
b7c53000-b7c55000 rwxp b7c53000 00:00 0 
b7c55000-b7c56000 rw-p b7c55000 00:00 0 
b7c56000-b7c5e000 r-xp 00000000 08:01 3412478    /usr/lib/libstartup-notification-1.so.0.0.0
b7c5e000-b7c5f000 rw-p 00007000 08:01 3412478    /usr/lib/libstartup-notification-1.so.0.0.0
b7c5f000-b7d94000 r-xp 00000000 08:01 3412215    /usr/lib/libxml2.so.2.6.32
b7d94000-b7d95000 ---p 00135000 08:01 3412215    /usr/lib/libxml2.so.2.6.32
b7d95000-b7d99000 r--p 00135000 08:01 3412215    /usr/lib/libxml2.so.2.6.32
b7d99000-b7d9a000 rw-Aborted
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2c00027 specified for 0x2c06185 (Screen is ).

---

### Post by reahjw6 on 2009-01-03
Hey forlong sorry when i ran compiz my screen locked up
Compiz-check says all is ok.
Again i realy appreciate your time helping me out.
sorry for being a little dense in computer terms.

---

### Post by Forlong on 2009-01-03
> **reahjw6 said:**
> Compiz-check says all is ok.
It's the system info Compiz-Check provides I am looking for, so please post them here.

And use the forum's [noparse][CODE][/noparse] tag please.
It's the button that looks like a # that provides it when you are writing a post (don't use the Quick Reply, because it's not available there).

---

### Post by reahjw6 on 2009-01-03
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8500 GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2009-01-03
Alright, now what's the output of ```
dpkg -l | grep compiz
```

---

### Post by reahjw6 on 2009-01-03
reahjw6@reahjw6-desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.7.8-0ubuntu4.1                      OpenGL window and compositing manager
ii  compiz-core                                1:0.7.8-0ubuntu4.1                      OpenGL window and compositing manager
ii  compiz-fusion-bcop                         0.7.6-1ubuntu1                          Compiz Fusion option code generator
ii  compiz-fusion-plugins-extra                0.7.8-0ubuntu2                          Collection of extra plugins from OpenCompositing for Compiz
ii  compiz-fusion-plugins-main                 0.7.8-0ubuntu2.2                        Collection of plugins from OpenCompositing for Compiz
ii  compiz-gnome                               1:0.7.8-0ubuntu4.1                      OpenGL window and compositing manager - GNOME window decorator
ii  compiz-plugins                             1:0.7.8-0ubuntu4.1                      OpenGL window and compositing manager - plugins
ii  compiz-wrapper                             1:0.7.8-0ubuntu4.1                      OpenGL window and compositing manager, wrapper script
ii  compizconfig-backend-gconf                 0.7.8-0ubuntu1                          Settings library for plugins - OpenCompositing Project
ii  compizconfig-settings-manager              0.7.8-0ubuntu3                          Compiz configuration settings manager
ii  libcompizconfig0                           0.7.8-0ubuntu2                          Settings library for plugins - OpenCompositing Project
ii  python-compizconfig                        0.7.8-0ubuntu1                          Compiz configuration system bindings
reahjw6@reahjw6-desktop:~$

---

### Post by Forlong on 2009-01-03
Looks good to me, why do you have compiz-bcop installed? Did you try to install Compiz another way (e.g. by script)?

---

### Post by reahjw6 on 2009-01-03
Hey 
I have only installed from synaptic.
Thanks

---

### Post by reahjw6 on 2009-01-03
I have just looked and it is in the synaptic package should i uncheck this.
Again thankyou very much for your help.
Reah

---

### Post by Forlong on 2009-01-03
No, it's fine, I'm just stabbing in the dark here.

According to your setup, everything is fine. You might want to file a bugreport about this.

---

### Post by reahjw6 on 2009-01-03
Ok will mark as solved.
Have a good evening.

---

### Post by hypnojelly on 2011-10-05
So if I have:


Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GT218 [NVS 3100M] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

and

ii  compiz                                1:0.9.4+bzr20110415-0ubuntu2                 OpenGL window and compositing manager
ii  compiz-core                           1:0.9.4+bzr20110415-0ubuntu2                 OpenGL window and compositing manager
ii  compiz-gnome                          1:0.9.4+bzr20110415-0ubuntu2                 OpenGL window and compositing manager - GNOME window decorator
ii  compiz-plugins                        1:0.9.4+bzr20110415-0ubuntu2                 OpenGL window and compositing manager - plugins
ii  compiz-plugins-main                   0.9.4+bzr20110406-0ubuntu2                   Compiz Fusion plugins - main collection
ii  compizconfig-backend-gconf            0.9.2.4-0ubuntu1                             Compiz Fusion configuration system - gconf backend
ii  libcompizconfig0                      0.9.4-0ubuntu2                               Settings library for plugins - OpenCompositing Project
ii  python-compizconfig                   0.9.4-0ubuntu1                               Compizconfig bindings for python

...so I should file a bug report then too? :s Because I can click the blue compiz icon, but no menu is appearing. Reason I want to check out compiz is because my window headers have disappeared. In the thread ["[SOLVED] Window Header Disappears"]("http://ubuntuforums.org/showthread.php?t=1526589") it seems compiz is the origin of the problem...

---

