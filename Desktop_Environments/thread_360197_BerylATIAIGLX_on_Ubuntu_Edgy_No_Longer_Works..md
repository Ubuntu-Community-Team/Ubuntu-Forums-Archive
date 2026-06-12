---
title: "Beryl/ATI/AIGLX on Ubuntu Edgy No Longer Works."
date: 2007-02-12
forum: Desktop Environments
---

### Post by H0SS on 2007-02-12
So I used the install script from here [http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html) which worked perfectly the first time.  I was playing around with Wallpaper Manager in the Desktop Settings for the Beryl Manager.  After not getting an success with the wall papers I decided to just disable it and remove the images.  After doing this I lost the ability to manipulate the cube, (i.e. Ctrl + Shift + Left or Right) no longer rotate the cube.  The key sequence does nothing.  I know that the manager is working as I have the icon on the tray.  Any suggestions?

I also did a removal and re-installation of Beryl per the above web site's instruction.

---

### Post by shareMenaPeace on 2007-02-12
Hmm try my reinstall guide - see signature.

---

### Post by Danyl on 2007-02-12
> **H0SS said:**
> So I used the install script from here [http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html) which worked perfectly the first time.  I was playing around with Wallpaper Manager in the Desktop Settings for the Beryl Manager.  After not getting an success with the wall papers I decided to just disable it and remove the images.  After doing this I lost the ability to manipulate the cube, (i.e. Ctrl + Shift + Left or Right) no longer rotate the cube.  The key sequence does nothing.  I know that the manager is working as I have the icon on the tray.  Any suggestions?

I also did a removal and re-installation of Beryl per the above web site's instruction.

I am experiencing the EXACT same problem as we speak! Scary...only I was playing with the cube.

Now I too have lost cube movement altogether and the Emerald/Beryl icon is in the tray also.

When I type:

```
beryl
```

into a terminal I get the following:

```
**************************************************************
* Beryl system compatibility check                           *
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
```

What's going on?

---

### Post by rwyankees on 2007-02-12
I have the same problerm ... I have been using beryl all day... and now I when i right click the jewel I can't click settings manager and when I select beryl as my windows manager it flickers and reverts back to normal... when I type beryl in terminal I get this :

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Segmentation fault (core dumped)

it has worked all day long till about 10 min ago

---

### Post by H0SS on 2007-02-12
The un-install instructions did the trick.  Thanks.

---

### Post by Danyl on 2007-02-12
> **rwyankees said:**
> I have been using beryl all day... and now I when i right click the jewel I can't click settings manager and when I select beryl as my windows manager it flickers and reverts back to normal... 

Ditto. This is weird.

---

### Post by H0SS on 2007-02-12
On a side note, is there a way to make the desktop transparent at all times, not just when rotating the cube?

---

### Post by H0SS on 2007-02-12
nm, I found it, lol

---

### Post by rwyankees on 2007-02-12
the uninstall thing worked..... how did you make the desktop transparent without rotating the cube?  just Alt+Mouse Wheel?

---

