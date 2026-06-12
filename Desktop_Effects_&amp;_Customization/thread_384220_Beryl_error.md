---
title: "Beryl error"
date: 2007-03-14
forum: Desktop Effects &amp; Customization
---

### Post by jayflower on 2007-03-14
I have the following error output in console after installing beryl.
I dont know what I miss, Ive installed Openchrome (following this step by step guide [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)) I appreciate any help)
My videocard is a generic s3 via.
Thanks.

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

libGL warning: 3D driver claims to not support visual 0x46
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
libGL warning: 3D driver claims to not support visual 0x46
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by FredB on 2007-03-14
Are you sure your hardware is working with beryl ? Because, following information for wiki beryl I can see :

Entering in google "beryl supported hardware" gives me this page :

[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL)

So look, with a little luck...

---

