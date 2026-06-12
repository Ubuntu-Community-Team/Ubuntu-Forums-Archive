---
title: "Open Gl Direct Rendering"
date: 2006-09-04
forum: Desktop Environments
---

### Post by hraposo on 2006-09-04
How can I activate Open Gl Direct Rendering to my geforce video card?

---

### Post by halfvolle melk on 2006-09-04
Something like this if it's a recent card.
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```
For old cards you'll need the legacy drivers.
See here for more details:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://www.ubuntuforums.org/showthread.php?t=98456](http://www.ubuntuforums.org/showthread.php?t=98456)

---

