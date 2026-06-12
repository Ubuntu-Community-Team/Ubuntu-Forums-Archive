---
title: "Creating a symbolic link"
date: 2009-03-13
forum: Desktop Environments
---

### Post by sharathpaps on 2009-03-13
Hi,
    I'm trying to compile the qc-usb drivers in Ubuntu Intrepid Ibex so that I can use a Logitech Quickcam. An extract from the instructions on their [webpage]("http://qce-ga.sourceforge.net/") :

The following requirements must be met:

    ```
* Kernel >= 2.2.18, kernel 2.4.x, or kernel 2.6.x with USB and V4L support. If you are running a version 2.2 kernel, you really need to upgrade to at least 2.4.
    *** Kernel source for the kernel you are running. The symbolic link /lib/modules/`uname -r`/build should point to the source directory.**
    * A working installation of gcc >= 2.95

```

How do I create the symbolic link /lib/modules/'uname -r' /build point to the source directory?

is something to be substituted for 'uname -r' and 'build' ?

---

