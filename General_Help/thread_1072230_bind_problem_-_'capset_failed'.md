---
title: "bind problem - 'capset: failed'"
date: 2009-02-17
forum: General Help
---

### Post by DannyG on 2009-02-17
Hi,

I'm trying to get bind9 running on a server I've just recently acquired which is running Ubuntu 8.04, but I seem to be having the following problem when trying to start bind9:

```
root@carina:~# /etc/init.d/bind9 start
 * Starting domain name service... bind
named: capset failed: Operation not permitted: please ensure that the capset kernel module is loaded.  see insmod(8)
   ...fail!
root@carina:~# 
```

A bit of google'ing tells me this is because the 'capabilities' kernel module is not loaded. So I try to run:

```
root@carina:~# modprobe capabilities
```

But this comes back with:

```
FATAL: Module capabilities not found.
```

I'm running kernel:

```
root@carina:~# uname -r
2.6.26-default

```

I've also checked my '/boot/config-2.6.26-default' to see if the correct parameters have been set at startup, and have the following:

```
CONFIG_SECURITY=y
CONFIG_SECURITY_CAPABILITIES=y
```

But even after a restart, nothing changes.

So, as near as I can tell, it seems like bind9 requires the 'capabilities' kernel module, which in turn seems to be missing from my system.

Does anyone have any ideas on how I can install this module or fix this problem? I have read that I can compile bind9 from source and give it parameter that would make it no need the capabilities module in the first place, but I'd much rather have it just to avoid any future problems.

Any help would be great.

---

### Post by ikonia on 2009-02-17
you're not using the ubuntu stock kernel - move back to the ubuntu stock kernel and I bet it starts working

---

### Post by Titan8990 on 2009-02-17
Also, to add to that, running Ubuntu on a vanilla kernel will almost never work right. There are other (non-debian) distros that have much better support for vanilla kernels but then you lost many of the "automagic" features of Ubuntu. 

Many modules and applications are patched to work properly with the modified Ubuntu kernel.

---

