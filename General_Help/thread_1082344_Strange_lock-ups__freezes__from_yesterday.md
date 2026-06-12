---
title: "Strange lock-ups / freezes  from yesterday"
date: 2009-02-27
forum: General Help
---

### Post by cherva on 2009-02-27
I have been experiencing strange, random lock-ups/freezes from yesterday. The first freeze was when I was playing Counter Strike with wine 1.1.5... then I started freezing at random bases ... in firefox (watching a flash video in a site), in mplayer while watching a video, on a simple desktop (nothing running ). Please help to diagnose this... 
I did't patched or installed anything when the freezing started.
All the logs I checked are clear of errors, dmesg is clear too,
/var/log/massages - clear....:confused::confused::confused:

---

### Post by BGFG on 2009-02-27
Did you upgrade video drivers recently? Seems display related....not sure if you are Nvidia or ATI though.

---

### Post by dsmithnc on 2009-02-27
I just discovered this morning that my ATI driver was causing my 8.10 installation to freeze constantly.  Removed it and all seems to be well, time will tell.

Dick

---

### Post by cherva on 2009-02-28
I'm using nvidia and I thing that I recently enabled monitoring in nvidia-settings. But I'm not quite shure... I'll checkit when I get home.

---

### Post by cherva on 2009-02-28
Sadly the monitoring is turned off ... any other ideas ? When my sister logs in, ubuntu do not freeze.
I tried with NVIDIA driver version 173.14.12 and it's ok now :)

---

