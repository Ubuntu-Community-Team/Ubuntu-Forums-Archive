---
title: "Having issues setting up desktop effects"
date: 2009-02-08
forum: General Help
---

### Post by khaji00 on 2009-02-08
Hello,

I just did a fresh install of 8.10 and originally had desktop effects running, but when i installed the latest ATI driver i seemed to have lost all the effects.  I ran compiz-check and go the following results:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M22 [Mobility Radeon X300]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect fglrx driver version in use.
```

I dont really understand what this has yielded other than the fact i "failed" some tests.  Can someone point me in the right direction to make changes and enable compiz-fusion effects.

Also,  i ran the command for blacklisted cards before even checking to see if my card was blacklisted, probably not a good idea but i couldnt figure the issue out.

Thanks

---

### Post by Wartender on 2009-02-08
do you have drivers installed for your graphics card?
try going to hardware drivers and seeing if there are any available for it

---

