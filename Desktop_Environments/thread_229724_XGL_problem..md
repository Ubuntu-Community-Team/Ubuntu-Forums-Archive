---
title: "XGL problem."
date: 2006-08-04
forum: Desktop Environments
---

### Post by jugo23 on 2006-08-04
I followed the guide on installing XGL on the forum and everything worked up until i got this error.

(II) Primary Device is: PCI 03:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:3:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found

Any help would be great.

---

### Post by jugo23 on 2006-08-05
no one know how to fix this?

---

### Post by chavo on 2006-08-05
Did you ever have 3d acceleration working? That error has nothing to do with XGL, it comes from the binary nvidia driver. If you did have it working perhaps a recent kernel update has made this prop up. Try rebooting into your new kernal and make sure that you update nvidia-glx as well.

---

