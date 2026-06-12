---
title: "libusb 1.0"
date: 2009-03-11
forum: General Help
---

### Post by biggyhigi on 2009-03-11
I have installed libusb 1.0 to my computer.  After initially installing it, I compiled some of the example programs and everything seemed to be working.  The next day, I tried to compile the program again and it was not able to find the libusb/libusb.h headerfile.  Does anyone know why this is happening?

---

### Post by geraldm on 2009-03-11
Could it be that the proper path is /usr/{local/}include/libusb-1.0/libusb.h?
If you expect it to find the header, you may have to pass the location to it.
If you did not reboot overnight, you may have to run sudo ldconfig before
configure/compiling.

regards,
Gerald

---

