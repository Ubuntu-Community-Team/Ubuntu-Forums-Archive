---
title: "Beryl + ATI FireGL T2 + Feisty + AIGXL Problems. Help."
date: 2007-04-12
forum: Desktop Environments
---

### Post by woocc on 2007-04-12
[COLOR="Red"]**Beryl**[/COLOR] doesn't work in my Ubuntu Feisty. I have all the packages installed. The composite driver is [COLOR="Red"]**AIGXL,**[/COLOR] the video card is: [COLOR="Red"]**ATI FireGL Mobility T2**[/COLOR]
(VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] )

**[COLOR="Red"]1) [/COLOR]**If I disable composite in xorg:
Direct rending works, however, when I start beryl, got the following error messge:
*************************************************
Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
*************************************************

**[COLOR="Red"]2) [/COLOR]**If I enable composite in xorg:
Direct rending doesnt work, and there're more errors:
*************************************************
 Detected xserver                                : AIGLX

 Checking Display :0.0 ...

 Checking for XComposite extension               : passed (v0.3)
  Checking for XDamage extension                  : passed
  Checking for RandR extension                    : passed
  Checking for XSync extension                    : passed

  Checking Screen 0 ...

  Checking for GLX_SGIX_fbconfig                  : passed
  Checking for GLX_EXT_texture_from_pixmap        : passed
  Xlib:  extension "XFree86-DRI" missing on display ":0.0".
  Checking for non power of two texture support   : failed

  Support for non power of two textures missing
  Xlib:  extension "XFree86-DRI" missing on display ":0.0".
  beryl: glXBindTexImageEXT is missing
  beryl: Failed to manage screen: 0
  beryl: No manageable screens found on display :0.0
  cc@CELL:~$ glxinfo | grep direct
  Xlib:  extension "XFree86-DRI" missing on display ":0.0".
  direct rendering: No
  OpenGL renderer string: Mesa GLX Indirect
*************************************************

Anyone has ideas?
Thanks,
-C

---

### Post by 00arthuryu on 2007-04-18
a suggestion might be to use XGL instead as i've heard ati and AIGLX doesn't work really well

---

### Post by octoberdan on 2007-04-21
Have you seen
[http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty) ?
I think you may be having problems with your drivers. Test with fgl_glxgears and fglrxinfo

---

