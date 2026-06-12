---
title: "dependency problems now not able to install or remove any package"
date: 2013-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by manish4362 on 2013-11-04
I was installing wvdial, now I do not need that, but because  of that machine got problem with dependencies, and due to that I am  unable to install any package, please help, Below is my stack trace: 
  The following packages have unmet dependencies:
  libqt3-mt:i386: Depends: libjpeg62 but it is not installed libusb-dev: Depends: libusb-0.1-4 (= 2:0.1.12-14) but 2:0.1.12-20 is installed dependency problems:i386: Depends: libc6 (>= 2.4) but 2.15-0ubuntu10.4 is installed              Depends: libuniconf4.4 but it is not installed              Depends: libwvstreams4.4-base but it is not installed              Depends: libwvstreams4.4-extras but it is not installed              Depends: libxplc0.3.13 but it is not installed              Depends: ppp (>= 2.3.0) but it is not installed

---

### Post by urapain on 2013-11-05
try holding down shift key during boot and select different kernel
If that works, see other posts for how to remove kernels or go back to a previous one.

---

### Post by Bucky Ball on 2013-11-05
Try, in a terminal:
```

sudo apt-get autoremove
```

Then:

```
sudo apt-get update
```

---

