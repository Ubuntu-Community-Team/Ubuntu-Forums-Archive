---
title: "Register dll"
date: 2008-08-09
forum: Desktop Environments
---

### Post by quikone8 on 2008-08-09
Wine wantts me to install and register dll, how do I do that, is there a syntax to get this accomplished?  That is, I have the dll in the fake system 32 folder, but I don't know how to register them.

---

### Post by wdaniels on 2008-08-09
If you mean a DLL "override" in Wine, you can do that from the Libraries tab in winecfg:

```
winecfg
```

Or if you mean to "register" (as in a COM DLL), you can do it the same way as in Windows, using the regsvr32 program:

```
wine cmd
regsvr32 C:\windows\system32\<COM_DLL>.dll
```

(unless someone knows an easier Wine-specific method)

---

### Post by quikone8 on 2008-08-09
Thanks, that worked very well.  Next problem; I get the following error when I try to start TVersity throught Wine:  Runtime Error!  Program C:...
R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.

The to Bar says:  Microsoft Visual C++ Runtime Library

---

### Post by therealwillie on 2008-08-21
> **quikone8 said:**
> Thanks, that worked very well.  Next problem; I get the following error when I try to start TVersity throught Wine:  Runtime Error!  Program C:...
R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.

The to Bar says:  Microsoft Visual C++ Runtime Library

having the exact same problem as i speak.... maybe its just me being a noob or maybe it just won't work... i dunno. i've tried mediatomb aswell but it says every file is not compatible with my ps3, even mp3's!

---

### Post by quikone8 on 2008-11-08
I hated to do it, but I went back to the flag virus software until someone develops tversity or media tomb that works in a deb format.

---

