---
title: "Driver for Intel 945GM graphics controller"
date: 2013-05-29
forum: Desktop Environments
---

### Post by williepabon on 2013-05-29
My Sony Vaio VGN-N130G has the following graphics-


```
williepabon@Precision-WorkStation-670:~$ sudo lshw -short
H/W path Device Class Description
===========================================================
......
/0/100/2 display Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
/0/100/2.1 display Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
```

I know that my Ubuntu 12.04 comes with Intel drivers for it, but for some reason it is running in 2D mode. As shown above, the OS recognizes the hardware. I ran the following commands that may indicate a problem, but is beyond my knowledge.


```
williepabon@Precision-WorkStation-670:~$ lsmod | grep video
video                  19115  1 i915

williepabon@Precision-WorkStation-670:~$ glxinfo | grep render
Xlib:  extension "NV-GLX" missing on display ":0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Intel(R) 945GM x86/MMX/SSE2
```

Anybody that can help to recover 3D mode will be really appreciated. Thanks.

---

### Post by Grafens on 2013-05-30
What happens when you type
> :~$ glxgearsfrom the console.
If you get a few gears running on the screen then you should have 3d accelertion. But for old video cards 3d accelertion is  probably not a good idea as it will draw on too much resources.

---

### Post by williepabon on 2013-05-30
@Grafens:

I get the gears alright, but also the following message:

```
williepabon@Precision-WorkStation-670:~$ glxgears
Xlib:  extension "NV-GLX" missing on display ":0.0"

```

There's something strange, since I have a strange behavior from my keyboard. The Fn key is running backwards! To type the letters U,I,O,P, etc, (where the numbers pad are located on a laptop) I have to press Fn first. Fn is to get the numbers!. I guess this is all related to the X11 system, but I'm not familiar with this. Advice on this is appreciated.

---

### Post by Grafens on 2013-05-31
> [COLOR=#000000]I have a strange behaviour from my keyboard. The Fn key is running backwards![/COLOR]
That's very familiar. I once installed mesa-something-or-the-other while trying to configure my laptop to run a program and that same thing happened to me (dell inspiron mini) never worked out how to fix it though just did a clean install of kubuntu. But as far as I remember the keyboard worked fine apart from the fn key doing things in reverse.
Supported/Deprecated Systems and Drivers
[http://www.mesa3d.org/systems.html](http://www.mesa3d.org/systems.html)

Personally I think this is more to do with intel than mesa/x11 but thats just my guess.
> Obsolete ReleasesDistribution    Last Supported Graphics Stack Release    Effective End-of-Life Date
Ubuntu* 12.04    2012Q4    Ubuntu* 13.04 was released in late April 2013. Support for Ubuntu* 12.04 effectively ended when the Intel® Linux* Graphics Installer version 1.0.1 was released (20 May 2013).
[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1)
All I can suggest is to install ubuntu 13.04
Please post if you get fixed
Grafens

---

### Post by williepabon on 2013-05-31
Grafens said:
> [https://01.org/linuxgraphics/downloa...-version-1.0.1]("https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1")
[COLOR=#000000]All I can suggest is to install ubuntu 13.04[/COLOR]
[COLOR=#000000]Please post if you get fixed[/COLOR]

I'm sticking with 12.04. Until I find a solution to use Unity 3D, I'm reverting to the GNOME GUI. It works fine, fast and does most of I need to do from a desktop. Thanks for all the help.
wp

---

