---
title: "Gimp won't start (gvfs-fuse-daemon in futex_wait)"
date: 2009-05-06
forum: General Help
---

### Post by arvana on 2009-05-06
I can't get Gimp to start on my fresh Jaunty 9.04 installation.  It has been working fine since my upgrade to Jaunty, until today.  

Checking my System monitor I notice that gvfs-fuse-daemon is stuck in futex-wait -- I'm not sure if that is the cause or not.  I have tried disabling all non-essential startup programs, but it is already in futex_wait immediately after reboot.

The only things I remember installing before it stopped working were btnx and revoco for my Revolution MX mouse, however I have tried uninstalling those and rebooting, with no success.

How can I discover why gvfs-fuse-daemon is hanging, and whether that is causing Gimp not to start, or if there is another reason why Gimp isn't working?

Many thanks!

---

### Post by cariboo on 2009-05-06
The gvfs-fuse daemon is needed to mount network shares, do you have a share that is hanging?

---

