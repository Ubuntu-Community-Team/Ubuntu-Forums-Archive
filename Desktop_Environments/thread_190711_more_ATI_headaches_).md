---
title: "more ATI headaches :)"
date: 2006-06-06
forum: Desktop Environments
---

### Post by evilhomer on 2006-06-06
i have the 8.24.8 driver installed properly, acceleration is working.  but there's some odd things when trying XGL, etc.  i found a common problem (according to google) in my x.org log, but no fix!

drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card89
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

repeated 254 times...

the module loads correct, etc.  i can't believe there's not more people with this issue.  so i figure someone has the solution?

edit: it doesn't repeat exactly that 254 times.  the card # goes up by 1 each time.

---

