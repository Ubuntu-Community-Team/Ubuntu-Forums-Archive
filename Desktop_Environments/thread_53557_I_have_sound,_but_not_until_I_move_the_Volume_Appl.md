---
title: "I have sound, but not until I move the Volume Applet slider at least once."
date: 2005-08-01
forum: Desktop Environments
---

### Post by jtp51 on 2005-08-01
I can live with this, however I was wondering if anyone else had an odd issue that they do not have any sound until the volume slider (Volume Applet 2.10.1) is moved up and down just once. Afterwards no issues at all...

Again, not a big deal, just kinda odd.

And yes, under System -> Sound preferences -> General tab; I have checked 'Enable sound server startup'.

Thanks!

---

### Post by Perfect Storm on 2005-08-01
[QUOTE=jtp51]I can live with this, however I was wondering if anyone else had an odd issue that they do not have any sound until the volume slider (Volume Applet 2.10.1) is moved up and down just once. Afterwards no issues at all...

Again, not a big deal, just kinda odd.

And yes, under System -> Sound preferences -> General tab; I have checked 'Enable sound server startup'.

Thanks![/QUOTE]

Try in the terminal:
```
alsamixer
``` 

And check out if something is turned off there.

---

