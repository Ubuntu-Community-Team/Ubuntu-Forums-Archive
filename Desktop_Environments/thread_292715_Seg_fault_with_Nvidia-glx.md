---
title: "Seg fault with Nvidia-glx"
date: 2006-11-04
forum: Desktop Environments
---

### Post by theplatypus on 2006-11-04
This morning the update manager gave notice that a few packages needed updating one of which was NVIDIA-GLX. I ran the updates without a problem, but upon running glxgears I get the following error. Any ideas how to fix this?

> glxgears
Error:API mismatch: the NVIDIA kernel module has the version 1.0-8762, but this client has the version 1.0-8776. Please make sure that the kernel module and all NVIDIA driver components have the same version.
Segmentation fault

---

### Post by theplatypus on 2006-11-04
anyone?

---

### Post by ubman on 2006-11-04
> **theplatypus said:**
> anyone?

same here?](*,)

---

### Post by chrisccoulson on 2006-11-04
I was prompted to update nvidia-glx and linux-restricted-modules on my Dapper machine this morning, but the update broke my X server. Here is the contents of /var/log/gdm/:0.log
```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux chris 2.6.15-26-amd64-k8 #1 SMP PREEMPT Fri Sep 8 20:14:40 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  4 17:01:28 2006
(==) Using config file: "/etc/X11/xorg.conf"
Error: API mismatch: the NVIDIA kernel module has the version 1.0-8762, but
this X module has the version 1.0-8776.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Rolling back nvidia-glx to 8762 fixes my problem

---

