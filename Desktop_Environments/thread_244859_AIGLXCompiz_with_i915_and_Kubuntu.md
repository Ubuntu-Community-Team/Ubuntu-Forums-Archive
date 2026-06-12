---
title: "AIGLX/Compiz with i915 and Kubuntu"
date: 2006-08-27
forum: Desktop Environments
---

### Post by obi-nine on 2006-08-27
Hi folks,

I've spent most of the day trying to eyecandify my computer but have only managed to get so far as:

- boot into KDE but without any windows borders or the ability to drag applications

- i can run kwin which gives me back my normal use

- when i run flxgears it crashes saying:

[I]libGL warning: 3D driver claims to not support visual 0x5b
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted[/I]

- when i kill kwin and try to run compiz (from konsole) it tells me:

[I]libGL warning: 3D driver claims to not support visual 0x5b
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0
[/I]

Any ideas??

many thanks,

obi9

ps. I'm using Xorg-air and when I do (even with kwin running):

**ps ax | grep compiz** 

I get:

 [I]5074 ?        S      0:00 kwrapper ksmserver --windowmanager compiz-start
 5076 ?        S      0:00 ksmserver [kdeinit] --windowmanager compiz-start
[/I]

---

### Post by Feänor on 2006-08-30
Post the steps that you follow to setup AIXGL and Compiz. I also tried install this on my centrino e the only Compiz didn't work for me too. But the glxgears works for me.

---

### Post by wlx on 2006-09-04
> libGL warning: 3D driver claims to not support visual 0x5b
I have this error, but I can run xgl and aiglx, with ubuntu edgy.

---

### Post by jshayden on 2006-09-18
> **obi-nine said:**
> 

[I]libGL warning: 3D driver claims to not support visual 0x5b
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted[/I]



I get the exact same error ever sience I installed XGL.  I have since given up on XGL but can't get rid of that error.

......?

Josh

---

