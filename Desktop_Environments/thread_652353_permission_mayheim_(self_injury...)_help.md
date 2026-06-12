---
title: "permission mayheim (self injury...) help"
date: 2007-12-28
forum: Desktop Environments
---

### Post by ndvndv on 2007-12-28
It's my fault... 
I've mistakenly shoot a chmod -r on the / directory causing all files to became root:root...
<laugh /> i've managed to rebuild mosty from this error, but at least some permissions are still uncorrects... for instance i'm not able to mount my usb stick and cdroms...

is anybody able to find a default permission map for a standard gutsy install (ubuntu 7.10) or are you able to suggest the right permissions for the mount command (or automount?)
Thanks in advance
NDV

---

### Post by p_quarles on 2007-12-28
The command chmod doesn't change ownership, it changes permissions settings. Did you just run the command by itself, or did you specificy a permission setting? 

Anyway, I'd advise you to proceed cautiously, and not to go changing too many settings without identifying the exact problem. If you can post the output of the following, it will help me get an idea where you are right now:
```
ls -l /dev | grep sd
```
This will get information specifically related to the USB issue.

---

