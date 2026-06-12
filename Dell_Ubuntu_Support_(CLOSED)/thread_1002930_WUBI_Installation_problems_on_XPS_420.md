---
title: "WUBI Installation problems on XPS 420"
date: 2008-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by foxmulder on 2008-12-05
Hi,

I have a Dell XPS 420 with a RAID 0 system. I have Vista Home.

I installed 8.10 Desktop version using WUBI, and this was ok.

When I try to boot into Ubuntu it tries to start to install itself, but it just halts with a busybox.

I have tried all boot options (safe etc.) but it always ends in the same way.

Maybe Ubuntu does not know how to handle my RAID system.

Is there a solution for this? Do I need to give extra parameters when booting?

Can install using WUBI but then use Ubuntu 8.1 Alternate?

---

### Post by foxmulder on 2008-12-06
Anyone?

---

### Post by foxmulder on 2008-12-07
Seems like no one knows **** around here.. very helpful forum - NOT!

---

### Post by smoky57 on 2008-12-27
No definitive answer I'm afraid but it is my guess that Wubi 8.10 doesn't support RAID (despite some documentation saying that this was planned for 8.10 release). See discussion in [http://ubuntuforums.org/showthread.php?t=999908](http://ubuntuforums.org/showthread.php?t=999908) which includes various opinions but no conclusion (yet).

Regards

---

### Post by slorkman on 2008-12-28
> **foxmulder said:**
> Seems like no one knows **** around here.. very helpful forum - NOT!

Hi Fox! I had the same problem you discribed. I wanted to dualboot my Vista64 machine wit Ubuntu64 8.10. I can work If you use the alternate installer. The alternate installer has support for the softraid adapter used in the XPS.

Hope this works for, I'm only a linux beginner, this took me at least an hour to figure out.

:lolflag:

---

