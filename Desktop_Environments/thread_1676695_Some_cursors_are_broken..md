---
title: "Some cursors are broken."
date: 2011-01-27
forum: Desktop Environments
---

### Post by poctob on 2011-01-27
After upgrade to 10.10 certain cursors became broken. Please see attached picture to get an idea what it looks like, I've circled the cursor.  I had to take a pic with a camera, if I do a print screen the resulting image shows normal cursor.  I've tried turning off desktop effects and different drivers for the video card.  The cursor is broken for the following apps:
rdesktop - always when connected to the remote host
chrome/firefox - image zoom in/out
open office draw - when I try to resize a line.

Thanks in advance

---

### Post by Frogs Hair on 2011-01-27
Hi , sorry , but I can't tell much by your picture. If they are cursors themes that you have download , they may no longer be compatible. I would check for updated versions if this is the case .

I have found themes , icons , and other things that simply don't work because the developer failed to keep them up to date.

---

### Post by poctob on 2011-01-28
> **Frogs Hair said:**
> Hi , sorry , but I can't tell much by your picture. If they are cursors themes that you have download , they may no longer be compatible. I would check for updated versions if this is the case .

I have found themes , icons , and other things that simply don't work because the developer failed to keep them up to date.

I actually never installed any custom cursor themes.  I've tried changing cursor in the theme customization screen without any success.  It is strange that it only affects a few apps.

---

### Post by scubasteve657 on 2011-09-02
I'm having the same problem, using an ATI Radeon HD 5450.  I run two monitors off the card, no problems on the DVI, only on the VGA.  

Seems to me to be a problem related to the card, and only with Rdesktop and maybe other full screen apps.

Anyone figure this out?  Really irritating to work with.

---

### Post by scubasteve657 on 2011-09-02
Got it!  Turns out installing the lastest version of the ATI driver from their site did the trick:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

