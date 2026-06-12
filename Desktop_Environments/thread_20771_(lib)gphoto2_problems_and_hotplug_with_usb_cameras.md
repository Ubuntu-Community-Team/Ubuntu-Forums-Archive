---
title: "(lib)gphoto2 problems and hotplug with usb cameras"
date: 2005-03-18
forum: Desktop Environments
---

### Post by ubuntulnx on 2005-03-18
how can i get the fotos of my usb camera? 

after inserting the camera and recognizing it, ubuntu is telling me to remove stv680 module, which i do. with sudo modprobe -r stv680. is disappears from lsmod list, but the problem continues. i have seen similar issues on other forums (and other distr. of linux), and it seems to me that hotplug does not give the correct r/w rights to the /proc/bus/usb ("it can't claim the device"). i have not seen any sollution so far.  the camera has full support from libgphoto2.

thanks!

---

