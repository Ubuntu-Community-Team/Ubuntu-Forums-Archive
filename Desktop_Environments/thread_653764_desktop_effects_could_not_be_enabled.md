---
title: "desktop effects could not be enabled"
date: 2007-12-30
forum: Desktop Environments
---

### Post by Guruprasad on 2007-12-30
Hi

I can not change the option in visual effects to anything other than none. 

Here is my compiz output.

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by erfahren on 2007-12-30
have you enabled the restricted driver (if any)? 

what kind of video card? (look for the VGA compatible controller line of):
```

lspci

```

---

