---
title: "Kernel Update problem"
date: 2009-01-16
forum: General Help
---

### Post by thefrozenpenguin on 2009-01-16
I have been using linux for quite a while now, and only recently with the advent of netbooks have non geeks been tempted by linux.  A colleague at work took that a step further and after getting his wife hooked on a Acer One he installed Ubuntu Intrepid on his HP laptop managing with no help to get it to dual boot with XP.

On the last round of updates one of the packages to be updated was the latest kernel but this message (part of it) appeared and has since stopped alowing him to update:

[INDENT]E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version
[/INDENT]
Anyone have any ideas what is the best way around this?

---

### Post by redilyn on 2009-01-16
Is he using a fat32 partition for ubuntu. If so, refer him to this bug report

[https://bugs.launchpad.net/wubi/+bug/252900](https://bugs.launchpad.net/wubi/+bug/252900)

---

### Post by thefrozenpenguin on 2009-01-16
I'm awaiting a response from him, though having checked the numerous copies of that bug I think he must have installed ubuntu via wubi.

---

