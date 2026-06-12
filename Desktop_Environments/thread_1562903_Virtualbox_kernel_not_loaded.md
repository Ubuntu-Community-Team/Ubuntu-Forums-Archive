---
title: "Virtualbox kernel not loaded"
date: 2010-08-28
forum: Desktop Environments
---

### Post by wbrokow1 on 2010-08-28
When I installed Virtualbox I get an error that the kernel module was not loaded. How can I remedy this?  I did many searches in the forum and no solutions work,  I am using ubuntu 8.04

Thanks for any help

---

### Post by warddr on 2010-08-28
Did you already restart your computer after installation?

---

### Post by hictio on 2010-08-28
What is the exact error message you are getting?

---

### Post by wbrokow1 on 2010-08-28
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by demosthenese on 2010-08-28
Whenever VirtualBox is upgraded, or your kernel is upgraded, you need to reinstall the driver.

```
sudo /etc/init.d/vboxdrv setup 
```

---

### Post by wbrokow1 on 2010-08-29
alex@alex-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
alex@alex-desktop:~$

---

### Post by wbrokow1 on 2010-08-31
Failure to create the Virtualbox COM object
terminate

any help is appreciated

---

