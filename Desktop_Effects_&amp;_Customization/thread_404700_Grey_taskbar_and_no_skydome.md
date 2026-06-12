---
title: "Grey taskbar and no skydome"
date: 2007-04-08
forum: Desktop Effects &amp; Customization
---

### Post by Narfi on 2007-04-08
Hi, just switched to ubuntu (edgy) and very new to linux :) . I successfully installed the drivers for my ATI 9600xt  and beryl using this script : [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI) just had to tweak the xorg.conf a little so all good . 
All the effect work great and the rotating cube is awesome but i have a small problem. I cant load a skybox, tried every solution i could found on the net and here but no resolution or format worked and the taskbar is not skin .I Made a screenshot to make myself clear : [click ]("http://img353.imageshack.us/my.php?image=screenshotjo6.png") See the grey taskbar ? A bit ugly :p 

Changing theme change the window bar but not the taskbar ... And when i run beryl in a terminal i got this : > **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0


I guess its somehow linked ? runing beryl-xgl dont show any error ...

Hope those are not noobish questions and sorry for my bad english :) .

---

### Post by jakev383 on 2007-04-08
> **Narfi said:**
> Hi, just switched to ubuntu (edgy) and very new to linux :) . I successfully installed the drivers for my ATI 9600xt  and beryl using this script : [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI) just had to tweak the xorg.conf a little so all good . 
All the effect work great and the rotating cube is awesome but i have a small problem. I cant load a skybox, tried every solution i could found on the net and here but no resolution or format worked and the taskbar is not skin .I Made a screenshot to make myself clear : [click ]("http://img353.imageshack.us/my.php?image=screenshotjo6.png") See the grey taskbar ? A bit ugly :p 

Changing theme change the window bar but not the taskbar ... And when i run beryl in a terminal i got this : 

Correct. That's the way mine works too. If you want to change the taskbar, right click it and select properties. You'll then be able to change the color and what not.
And I can't load a skybox either. I'm running version 0.2.0-SVN and when I try and load a cool picture it crashes Beryl on me. It's not 100% stable, so you have to live with what does work.

---

### Post by Narfi on 2007-04-08
ah well, at least i'am not alone, do you have the same output with beryl in a console ?

---

### Post by jakev383 on 2007-04-09
> **Narfi said:**
> ah well, at least i'am not alone, do you have the same output with beryl in a console ?
Mine's a little different:
```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 139 requests (138 known processed) with 0 events remaining.

```
Now on my desktop with a GeForce 6200 card I can run a skydome downloaded from NASA's website. That's not running a SVN version either, so that may make some difference. It'll be interesting to see what happens in the coming months with the re-merge between Beryl and Compiz.

---

### Post by Narfi on 2007-04-09
Shamless bump if anyone have a idea :)

---

### Post by dustigroove on 2007-06-16
[FONT=Arial][SIZE=2][COLOR=Black]Gonna have to bump this as well...  I am still searching out a fix to get the Skydome feature to work with XGL/Beryl/fglrx.

**EDIT:** Nevermind, I have since found [this thread]("http://ubuntuforums.org/showthread.php?t=301414&highlight=beryl+xgl+skydome+ati") that explains that there is a max texture size limit that i was bumping up against with my chosen skydome images.

Cheers

[/COLOR][/SIZE][/FONT]

---

