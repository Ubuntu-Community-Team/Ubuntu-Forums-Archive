---
title: "nVidia driver install error"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by Foxblood on 2007-10-21
hi, all, I just upgraded to Gutsy and everything appears ok except my nVidia drivers
 When I try to install I get this:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-xconfig

Can anyone bail me out? Thanks in advance.

---

### Post by FuturePilot on 2007-10-21
Try removing nvidia-xconfig
```
sudo apt-get remove --purge nvidia-xconfig
```

---

### Post by Foxblood on 2007-10-21
Thanks for the swift and accurate reply. Worked perfectly, thanks again..

---

### Post by FuturePilot on 2007-10-21
No problem:)

---

