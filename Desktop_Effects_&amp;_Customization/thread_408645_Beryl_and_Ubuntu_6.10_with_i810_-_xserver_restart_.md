---
title: "Beryl and Ubuntu 6.10 with i810 - xserver restart loop"
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by azreal4066 on 2007-04-13
Hello,

I am fairly new to debian linux and I have come across a problem loading Beryl that I can't seem to find an explanation for.  I have Ubuntu 6.10 and am using Beryl, installed from the most recent edgy package with an Intel i810 chipset.  The install went smooth and without any errors and when I launch beryl I get a full pass.  
Here is the output from launching beryl:
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

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
```
Which seems to lead one to believe that it is running successfully.  However, whenever I invoke beryl, it restarts my xsession and dumps me back onto a login screen and when I login back in, no beryl.  No icon in the tray, no effects, nothing but standard gnome.  If I add the session scripts to automatically launch the manager as the installation says, then I login and it restarts the xsession and dumps me back at a login again trying to load beryl and I have to reconfigure my session scripts just to get to a desktop and out of the loop.  I don't know where to go from here.  I'm not sure where to even start looking.  I have scoured many forums and FAQ's looking for a hint and I haven't found much help.  I know there must be some deep rooted evil in the fact that the chipset is an Intel, but I don't have much of a choice for hardware at the moment.  I figured here would be a place to start.  I have noticed, however, than when I launch beryl and it loops back to a login it does shutdown metacity; it just doesn't replace it with beryl.

---

