---
title: "Problems with XGL/Beryl"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by rogeriovinhal on 2007-04-19
Hi, I have some problems with XGL/Beryl in my ATI card.

Everything worked fine on Edgy, but now some things are not working.

When I log into XGL session, fglrxinfo returns "Radeon 9600XT", everything where it should be. But when I try glxinfo, it says there is no direct rendering.

Maybe thats why when I run beryl in terminal, I get this:

```

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

I managed to make Beryl work with ati open source drivers, but I think it is a little slower than it was on XGL, so I want to make it work on XGL also.

I am using the restricted drivers to use fglrx. Is there something else I should do to enable beryl?

---

### Post by rogeriovinhal on 2007-04-20
UP.

Anyone with XGL/Beryl with fglrx or everyone is using open source drivers and AIGLX?

---

