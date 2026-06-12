---
title: "kubuntu + beryl doesn't work &gt;&lt;"
date: 2007-04-26
forum: Desktop Environments
---

### Post by tsung_cheng on 2007-04-26
after apt-get install beryl in my kubuntu,
and run the beryl,
the error log show up...
does someone has any idea??
tks~!

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
Checking maximum texture size                   : failed

Root window size (2304/1024) is bigger then maximum texture size (2048x2048)

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  34
  Current serial number in output stream:  36

---

### Post by srouquette on 2007-04-27
> Root window size (2304/1024) is bigger then maximum texture size (2048x2048 )
maybe you are using a dual screen, and Beryl dosen't like it...

---

### Post by tsung_cheng on 2007-04-28
oops...

:( 

anyway, tks for ur kindly help ~!

---

