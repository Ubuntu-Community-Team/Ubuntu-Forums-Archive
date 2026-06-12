---
title: "&quot;OS&quot; Partition no Longer Password Protected"
date: 2009-04-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by floborg on 2009-04-07
Initially, the "OS" partition (which appears to have the Dell recovery DVD contents) was only accessible by root.  I did something, and now I can just mount it by clicking on it in Nautilus.  I can't find an option to re-protect that parition.  Where should I be looking?

---

### Post by floborg on 2009-04-30
Wow, what a flood of responses!  :P

Here's how I reverted to the old behavior:

System => Administration => Authorizations

From there, select:

org => freedesktop => hal => storage => Mount filesystems from internal drives.

In the **Explicit Authorizations** area, I removed my user account by selecting Revoke.

---

