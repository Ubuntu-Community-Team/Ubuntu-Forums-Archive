---
title: "beryl + xgl post installation problems"
date: 2007-02-13
forum: Desktop Environments
---

### Post by linex on 2007-02-13
i finally got beryl working with xgl, in my gateway with the ati xpress 200m.
the first time i used it, it looked great. i loved the way it looked and the way it worked was close to perfect.
once i restarted and went back to xgl, everything seems to be messed up. it loads okay but as soon as i open an application, the screen goes crazy for couple seconds.
once going to command prompt i typed in beryl and here's what i get back:
> lin@Terminal777:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0
lin@Terminal777:~$ beryl-manager
lin@Terminal777:~$ 

the bottom toolbar also disappreas and none of the effects, transparenty, changing desktops or anything work.

what am i doing wrong now?

thanks

edit: one more thing, when i go to turnoff button, there's no shutdown in xgl. is this normal?

---

### Post by Ubuntiac on 2007-02-17
Exactly the same here.

I'm using Beryl + fglrx +XGL.

---

