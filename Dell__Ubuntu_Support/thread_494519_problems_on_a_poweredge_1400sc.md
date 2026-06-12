---
title: "problems on a poweredge 1400sc"
date: 2007-07-07
forum: Dell  Ubuntu Support
---

### Post by untruestory on 2007-07-07
I just got an old poweredge 1400sc from a friend. I cannot seem to load the modules for any video card other than the onboard video at the same time as the module for the scsi adapter (aic7xxx.o) as it causes the system to freeze up. Any suggestions?

---

### Post by neptho on 2007-07-07
Try this:
```
%sudo -c 'echo "blacklist video" >> /etc/modprobe.d/blacklist'
```

Then, reboot the system and see if it starts magically working

---

### Post by untruestory on 2007-07-10
Nevermind I'm an idiot. I'm having a bunch of issues with this poweredge. Gonna just make it work and give it to a friend thanks for the try though.

---

