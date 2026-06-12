---
title: "Beryl Suddenly crash after SVN update"
date: 2007-02-19
forum: Desktop Environments
---

### Post by LostSouLz on 2007-02-19
Hi i've updated beryl to the 16th SVN release and my beryl suddenly crashes. I've uninstalled the 16th release and reinstalled to version 0.1.9999.2~0beryl1 and my beryl is still giving me errors..

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

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

Can someone enlighten me on how to get it fixed?

---

### Post by Jeremy23 on 2007-02-21
Are you using NVIDIA? In that case, you'll want to install the NVIDIA version 9631 drivers from: [http://www.albertomilone.com/driver_edgy.html](http://www.albertomilone.com/driver_edgy.html)

---

### Post by LostSouLz on 2007-02-21
> **Jeremy23 said:**
> Are you using NVIDIA? In that case, you'll want to install the NVIDIA version 9631 drivers from: [http://www.albertomilone.com/driver_edgy.html](http://www.albertomilone.com/driver_edgy.html)


Im using ATI X1400

---

### Post by Jaydude765 on 2007-02-21
I'm having a similar problem after the last SVN update. Its not that beryl completely crashed. I get a white screen. When i goto the cube view and the transparency kicks in, i can see all the windows, but nothing is textured... 

I also have a X1400 ati card, i'm on a Dell Inspiron 6400.

Is there an easy way to revert to the previous svn release form 2 days ago, that did work?

Thanks

---

### Post by hubert.muchalski on 2007-02-21
The same issue here

---

### Post by naseem on 2007-02-21
another here

---

### Post by Jaydude765 on 2007-02-21
I found this, it may be of use if you wish to downgrade to the last working version:

[http://forum.beryl-project.org/viewtopic.php?p=22898#p22898](http://forum.beryl-project.org/viewtopic.php?p=22898#p22898)

---

### Post by Jeremy23 on 2007-02-21
Well it definitely looks like a known issue, and there's not much you can do until they fix it. Perhaps you should be running off the stable repository instead - these issues are far less likely to occur.

---

### Post by mcduck on 2007-02-21
reading from Beryl forums it seems that this problem is in the stable version too. So there is only 2 options, either downgrade to older packages or wait until it gets fixed :)

---

