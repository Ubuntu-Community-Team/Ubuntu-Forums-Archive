---
title: "/dev audio not created"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Markpy on 2005-10-15
Hi, I've noticed that no audio device nodes are created during bootup. I have to manually:

```
cd /dev && sudo ./MAKEDEV audio
``` 
This is rather annoying. I tried adding a section to **/etc/init.d/makedev**:

```

if [ ! ls /dev | grep audio]; then
    cd /dev && ./MAKEDEV audio
fi
``` 

That does nothing, but then again I don't know bash scripting.

Could anyone help?

P.S. Could some mod move this to the Video & Sound forum

---

