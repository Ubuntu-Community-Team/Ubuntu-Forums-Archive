---
title: "Beryl died..."
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by Fayte2071 on 2007-06-04
Ok, I read the post already that looked like mine, but it was really answered. I installed Beryl last night, it was fine and happy. I got it all to work, it was awesome. Then, it suddenly died. Metacity went back on and none of the Beryl functions worked anymore. I right clicked the Beryl icon and went to 'Select Windows Manager' and clicked on Beryl. Now, my windows flashes but then goes back to Metacity; sort of like it's trying to go into Beryl but it won't. Any suggestions?

---

### Post by Ub1476 on 2007-06-04
If you are logged in in XGL, you most use Beryl v. 0.2.0.

---

### Post by LollYouSuckZor on 2007-06-04
I would suggest a new clean install..

---

### Post by Fayte2071 on 2007-06-04
> **Ub1476 said:**
> If you are logged in in XGL, you most use Beryl v. 0.2.0.

What's XGL?

And what kind of install? install ubuntu again?

---

### Post by Satanister on 2007-06-04
Try running it from the terminal and post the output.....

---

### Post by Fayte2071 on 2007-06-04
ok, i typed in beryl in the terminal and got this: 
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
Not a JPEG file: starts with 0x89 0x50

---

### Post by WaeV on 2007-06-04
You are using an nvidia card, yes?

XGL is one way to run beryl.  I think it involves setting up a separate X server for systems that don't want to cooperate with beryl.  Usually nvidia works so I am surprised by your output.  Unless the XGL server gives that output.  If you don't know what XGL is then your probably didn't use it.

I think LollYouSuckZor meant a clean install of beryl.

---

### Post by Fayte2071 on 2007-06-04
Ah ok. Now, how do i do a clean install of beryl? I go into the package manager and click on the beryl things and click 'check for complete removal' but that doesn't work. How do i go about a clean install?

---

