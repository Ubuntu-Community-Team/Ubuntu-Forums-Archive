---
title: "ATI 1650 GT Card, No desktop effect ?"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by lunziyu on 2007-04-20
My display card is ATI  1650 GT, and I installed the restricted driver in feitsy
but when i enable the effect, a dialog with "The composite extension is not availabe"comes out,
What should I do?
thx!

---

### Post by lunziyu on 2007-04-20
Anyone know how to solve this problem?

---

### Post by applefreakpeeps on 2007-04-20
Hi!
       You cant use default AIGLX enabled desktop effects as The fglrx drivers do not support Composite extension. Install XGL and beryl using apt-get and u can have all desktop effects up and running.

---

### Post by lunziyu on 2007-04-20
> **applefreakpeeps said:**
> Hi!
       You cant use default AIGLX enabled desktop effects as The fglrx drivers do not support Composite extension. Install XGL and beryl using apt-get and u can have all desktop effects up and running.

I have installed beryl now
but when I run command "beryl", it outputs the following message

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

---

### Post by lunziyu on 2007-04-20
ok, now i start a XGL session and the message changed, and all the title bars disappeared..
the message is as follow:

```
**************************************************************
* Beryl system compatiblity check                            *
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

```

---

