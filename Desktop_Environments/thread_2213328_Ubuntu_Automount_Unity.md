---
title: "Ubuntu Automount Unity"
date: 2014-03-26
forum: Desktop Environments
---

### Post by jon39 on 2014-03-26
Hi!

We are using Ubuntu 12.04 Desktop in a student lab. The homedirs are automounted from a samba-server.
After booting and login in in Unity, the homedirs of every student ever logged in on this computer are mounted.
Login in on the console (ctrl-alt-f1) or remote only mounts correctly the homedir of the logged in user...

I suspect that Unity remembers (and shows) every logged in user and shows it under "Switch User Account...." (which is an annoyance anyway).
and therefore mounts every homedir.

How do I get rid of this stupidy!

thanks

jon

---

### Post by TheFu on 2014-03-26
First - mounting a HOME via samba doesn't make sense. HOME dirs need UNIX permissions to be effective and NFS is the way to ensure that - NOT, NOT, NOT CIFS.

How many mount points are provided to the automouter?  If there is only 1 with all the student's HOMEs, then that will be what gets mounted. If you want ONLY the specific HOME, setup individual mounts.

It is possible to prevent any listings for the login screen via settings. How depends on the login manager used.  I use LXDE, so 
/etc/lxdm/ holds those configs.

Or am I misunderstanding?

Trying to fix anything else before the use of CIFS is like using a thimble to bail the Titanic, IMHO. Could it be that NFS is being used?

---

