---
title: "Only failsafe works"
date: 2008-05-20
forum: Desktop Environments
---

### Post by Sliver85 on 2008-05-20
So I installed kde to try it out, didn't like it, and am now switched back to Gnome.  The problem is the only way I can login is if I select Gnome Failsafe from the session selector.  Default and regular gnome simply bring me back to the login screen.

I am getting the following errors in my syslog:
```
May 20 20:13:24 mitchLinux gdm[24515]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 20 20:13:40 mitchLinux gdm[6022]: WARNING: gdm_cleanup_children: child 26617 crashed of signal 11 
May 20 20:13:40 mitchLinux gdm[6022]: WARNING: gdm_cleanup_children: Slave crashed, killing its children 
May 20 20:13:40 mitchLinux kernel: [142304.433690] gdm[26617]: segfault at 0000000c eip b78517e2 esp bfeeb6c0 error 6
May 20 20:13:53 mitchLinux kernel: [142310.826548] gdm[26654]: segfault at 0000000c eip b78517e2 esp bfeeb690 error 6
May 20 20:13:53 mitchLinux gdm[6022]: WARNING: gdm_cleanup_children: child 26654 crashed of signal 11 
May 20 20:13:53 mitchLinux gdm[6022]: WARNING: gdm_cleanup_children: Slave crashed, killing its children 
```

These all happen around the time I try to login but fail.

---

