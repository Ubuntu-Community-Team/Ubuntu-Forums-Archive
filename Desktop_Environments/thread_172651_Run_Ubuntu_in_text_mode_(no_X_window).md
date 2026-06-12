---
title: "Run Ubuntu in text mode (no X window)"
date: 2006-05-09
forum: Desktop Environments
---

### Post by _Chris_ on 2006-05-09
Greetings, 

I have installed Ubuntu 5.10 as a virtual machine in VMware Server.  The next step is to install VMware Tools, which enhance performance.  The instructions call for running [Ubuntu] in text mode only.  Can anyone point me in the right direction of how to achieve this.

These are the instructions:
"Be sure the guest operating system is running in text mode. You cannot install VMware Tools from a terminal in an X window session. Some recent distributions of Linux are configured to run the X server when they boot and do not provide an easy way to stop the X server. However, you can
switch to a different workspace that is still in text mode and install VMware Tools from that workspace."

Thanks, Chris

---

### Post by Reshin on 2006-05-09
```
sudo /etc/init.d/gdm stop
```
after installing:
```
sudo /etc/init.d/gdm start
```

---

