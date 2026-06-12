---
title: "Driver for scanner"
date: 2006-10-08
forum: Desktop Environments
---

### Post by cavillas on 2006-10-08
Has anyone come across the a driver for HP scanjet 3970?

---

### Post by VirgilCWolter on 2006-12-26
This link helped me get my HP 3970 working.
[http://www.ubuntuforums.org/showthread.php?t=288751&highlight=hp+3970](http://www.ubuntuforums.org/showthread.php?t=288751&highlight=hp+3970)
Also you need to find which file the scanner points to (I looked in the device manager) and then do the following:
sudo chmod a+w /dev/bus/usb/00X/00X (where X is the file numbers you find)
or cd //dev/bus/usb/00X
sudo chmod a+w 00X
Remember that X is not what you use here, replace the X with the number you find like 002.

---

