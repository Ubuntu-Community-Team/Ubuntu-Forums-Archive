---
title: "shutdown error system hangs"
date: 2005-12-21
forum: Desktop Environments
---

### Post by porsher_puddles on 2005-12-21
i haven't really got any other problems with breezy appart from this error on shutdown:
acpi-0508:*** error:method execution failed [\sb_ .pc10.1
deo-gtm] (node dffd79eo), ae-amc-package-limit
error evaluating -gtm

then the system hangs and i have to turn it off via the power button.
i can reboot and the system does that ok, its just when i go for shutdown i get the error.

any ideas out there.

---

### Post by 23meg on 2005-12-21
See if shutting down with the following commands changes anything:
```
sudo shutdown -P now
```
```
sudo shutdown -h now
```

---

### Post by srand on 2006-02-04
I seem to be suffering the same problem.. 

23meg using the 2 seperate commands the system shuts down by itself seemingly as normal (i.e. it switches itself off, as opposed to hanging using a straight shutdown -H command), however the last line printed before the power is switched off is still: Error Evaluating _GTM

Everything seems to be working fine, its a little annoying having the smae error occur without really knowing why its there..

---

