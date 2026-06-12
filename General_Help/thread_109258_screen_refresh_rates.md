---
title: "screen refresh rates"
date: 2005-12-28
forum: General Help
---

### Post by sabredog on 2005-12-28
Currently running Breezy at default resolution of 1024x768, which is fine. However the refresh rate of 60hz is inadequate for that resolution. 

There are no other refresh rates available however. :( 

Is there a fix for this at all?

cheers and thanks

---

### Post by Perfect Storm on 2005-12-28
```

sudo gedit /etc/X11/xorg.conf

```

Find the section called Section "Monitor". Under it you see:

HorizSync
VertRefresh

Find your monitor manual or google for your monitor specs and change it to the correct numbers.

Be warned: If you put the uncorrect numbers in, you can destroy your monitor.


reboot.

---

### Post by sabredog on 2005-12-28
A quick Google and data found.

An easy fix so many thanks. My eyes do not hurt so much now!

cheers and thanks

---

### Post by missmoondog on 2005-12-29
how do you go about making it stick to whatever setting? mine keeps goint up to 85 when i want it at 75.

---

### Post by missmoondog on 2005-12-31
bump!!

---

### Post by Irony on 2005-12-31
Go to;

*System > Preferences > Screen Resolution*

Tick;

*Make default for this computer only*

---

