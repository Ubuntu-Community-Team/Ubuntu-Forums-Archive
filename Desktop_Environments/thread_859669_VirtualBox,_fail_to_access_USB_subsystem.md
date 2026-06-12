---
title: "VirtualBox, fail to access USB subsystem"
date: 2008-07-14
forum: Desktop Environments
---

### Post by baosheng on 2008-07-14
Hi, I just downloaded Virtualbox for Ubuntu 7.10 from Sun's official website. But when i was trying to configure the USB filter list, I got a pop-up dialog window saying "Fail to access USB subsystem" and the following information:


```
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x00004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {f95c0793-7737-49a1-85d9-6da81097173b}


```

Does anyone know what I am supposed to do to fix this problem?

---

### Post by alfalfa31 on 2008-07-14
[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585)

---

### Post by chandra on 2008-07-16
See:

Ubuntu Unleashed: Howto: Install VirtualBox in Ubuntu Hardy Heron with USB Support in 5 easy Steps!

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

---

