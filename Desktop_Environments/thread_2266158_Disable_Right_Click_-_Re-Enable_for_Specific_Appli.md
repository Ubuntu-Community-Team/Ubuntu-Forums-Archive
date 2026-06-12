---
title: "Disable Right Click - Re-Enable for Specific Application"
date: 2015-02-20
forum: Desktop Environments
---

### Post by King of Heart 4711 on 2015-02-20
I'm in the process locking down an image to be rolled out to about 1800 clients running Ubuntu 14.04 x64 LTS with LXDE with the desktop. I need to disable right click on the mouse (which I can do with 

```
xmodmap -e "pointer =  1 2 99"
```

but this globally disables the mouse, we have an application that requires right click and I need to enable right click for that one application, but keep it disabled for everything else. Is this possible??

Many thanks!!!

---

