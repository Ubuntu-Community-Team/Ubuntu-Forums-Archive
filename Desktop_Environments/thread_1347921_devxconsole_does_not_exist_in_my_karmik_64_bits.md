---
title: "/dev/xconsole does not exist in my karmik 64 bits"
date: 2009-12-06
forum: Desktop Environments
---

### Post by PRDR on 2009-12-06
Hi,

Does anybody else have any troubles with the "xconsole" command?

When I launch that command in any of the 64-bit-kubuntu-karmik installations I have (those are the only karmik installations I have, actually), I get an error message related with the fact that /dev/xconsole does not exist. Which does not. But that did not use to happen in jaunty. I wonder why it is not being created. If I create it, it last until next reboot only...

I really do not know if this is a kubuntu-specific issue, or perhaps a 64-bit one...

I couldn't find any related posts, if I have missed something, I would appreciate it if someone points me to it.

Thanks in advance.

---

### Post by ladytux on 2009-12-29
Hi PRDR,

I have a 32bit Ubuntu Karmic and have the same issue as you. I found this temporary fix:

```

mknod -m 666 /dev/xconsole p

```.. then launching xconsole works.

I say temporary cause 1- I imagine I'll have to recreate it after a log off and 2- I know it's not suppose to run as root...
Hope it helps...at least short term :)

---

