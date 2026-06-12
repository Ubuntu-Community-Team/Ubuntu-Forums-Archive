---
title: "Searched threads and still cant fix... PLEASE HELP"
date: 2008-03-01
forum: Desktop Effects &amp; Customization
---

### Post by diirka on 2008-03-01
Ok first off I am pretty new to linux and dont know much but I love learning and that is my mission here.  I have just installed xubuntu 7.10 (was using ubuntu ultimate) and I cant get any of the compiz animations to work (i.e. cube, wabbly window ect.)  I have tried to enable the 3d graphics with ( glxinfo | grep direct ) but it says:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

Im not sure what video card my laptop has in it because I bought it used.  It is a dell inspiron 5100 if that helps.  Thanks in advance.

---

### Post by overdrank on 2008-03-01
> **diirka said:**
> Ok first off I am pretty new to linux and dont know much but I love learning and that is my mission here.  I have just installed xubuntu 7.10 (was using ubuntu ultimate) and I cant get any of the compiz animations to work (i.e. cube, wabbly window ect.)  I have tried to enable the 3d graphics with ( glxinfo | grep direct ) but it says:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

Im not sure what video card my laptop has in it because I bought it used.  It is a dell inspiron 5100 if that helps.  Thanks in advance.

HI and welcome, you can use the command lspci and this will list your hardware. Look for VGA and this will be your graphics card model. Then you can search and the info will help us also.

---

### Post by diirka on 2008-03-01
Thanks for the quick reply. Here is what it says:

ATI Technologies Inc Radeon Mobility M7 LW [Radeon Movility 7500]

---

### Post by rainwalker on 2008-03-02
To see if you can even use Compiz at all, try 
```
SKIP_CHECKS=yes compiz
```

---

