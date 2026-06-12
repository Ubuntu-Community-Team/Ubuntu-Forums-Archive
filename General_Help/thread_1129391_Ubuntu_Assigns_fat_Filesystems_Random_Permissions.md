---
title: "Ubuntu Assigns fat Filesystems Random Permissions?"
date: 2009-04-18
forum: General Help
---

### Post by Penguin Guy on 2009-04-18
Fat doesn't support Linux file permissions. So why on Earth does Linux assign it *random* permissions and owners!? Surely this can be avoided? This is a problem for my USB drive, but doesn't seem to affect my HDD.

Specifically, what is this a problem with? Just USB devices or all fat filesystems? Is this a bug? Is it possible to fix it?

It may be possible to fix this problem by editing some udev rules, you'll need to add something like: > **kevstar31 said:**
> mount umask=xxx uid=xxx gid=xxx

---

### Post by kevstar31 on 2009-04-18
mount umask=xxx uid=xxx gid=xxx

---

### Post by Penguin Guy on 2009-04-19
So I type that and it solves the problem? Could you please explain the code.

---

### Post by kevstar31 on 2009-04-19
try mounting with 
mount umask=000 uid=000 gid=000 /dev/*divice*

---

### Post by Penguin Guy on 2009-04-19
So every time I plug my USB drive in I've got to unmount it and then type that code in!? Thanks, but I will be eagerly waiting until this is fixed.

---

