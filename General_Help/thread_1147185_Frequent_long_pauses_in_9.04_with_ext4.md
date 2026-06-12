---
title: "Frequent long pauses in 9.04 with ext4"
date: 2009-05-03
forum: General Help
---

### Post by jowilkin on 2009-05-03
I am having frequent unacceptably long pauses in several applications in 9.04 64-bit with ext4.

It seems to be related to disk access.  I had experienced this with firefox periodically in 8.10, but now it is occurring in many applications and seems to be even longer.

Anyone else experiencing this?  Any possible solutions?

I converted from ext3 to ext4 if that may make a difference.

I've been using ext4 on my laptop with Arch Linux for a while now without this problem, but that was a clean install with ext4, not a conversion.

---

### Post by jowilkin on 2009-05-05
Formatted and installed Arch Linux, problem solved for now.  Using ext4 for / and xfs for /home.  Not sure what the problem was with Jaunty.  I am running it on my HTPC without issue.

---

