---
title: "Nvidia Help"
date: 2009-02-02
forum: General Help
---

### Post by dougmoser on 2009-02-02
I just installed Ubuntu on an older laptop and received a notification that I could install graphic drivers for the nvidia card inside of it.  So after I installed and rebooted I am being greeted by a black screen.  Does anyone know how to disable the driver without entering the OS?  The computer is a Toshiba 1415-S173.  Thanks all!

---

### Post by Crafty Kisses on 2009-02-02
Depending on what driver you grabbed you can run:
```
sudo apt-get remove --purge nvidia-glx-***
```
Where the stars are at, that should be your driver number (71,173,177,180).

---

