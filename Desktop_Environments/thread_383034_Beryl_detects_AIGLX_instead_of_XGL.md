---
title: "Beryl detects AIGLX instead of XGL"
date: 2007-03-12
forum: Desktop Environments
---

### Post by matemargo on 2007-03-12
I always get this error while trying to select Beryl as window manager:
```

Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
libberylsettings: dlopen: /usr/lib/beryl/libbench.so: cannot open shared object file: No such file or directory
beryl: No composite extension

```

I don't know why detects AIGLX as xserver instead of XGL. I've installed the package **xserver-xgl**.

And also there is a missing **libbench.so** library, where can I get it?

Thanks.

---

### Post by Waappu on 2007-03-13
Hi

Did you setup XGL session and login to that ?

You can find quite good instructions here end of this guide, but don't put Beryl to startup programs before you know it will work
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
__________________

---

### Post by matemargo on 2007-03-13
Yes, I do login to the XGL Session.

PS: The link doesn't work.

---

### Post by Waappu on 2007-03-13
Hi

I corrected link.

Starnge if Beryl still detect AIGXL
```
Detected xserver                                : AIGLX
```

See that guide I post and check do you have created session rigth and realy installed XGL

---

