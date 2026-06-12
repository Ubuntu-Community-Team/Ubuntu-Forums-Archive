---
title: "Can't shrink linux partition"
date: 2009-06-20
forum: General Help
---

### Post by TheHimself on 2009-06-20
I'd like to shrink the linux ext3 partition to make a new partition. When I run gparted using the Ubuntu (netbook remix) USB key, e2fsck does not give any errors but the command for shrinking keeps saying "Run e2fsck -f /dev/sda5 first." I don't know what's wrong.

---

### Post by jocko on 2009-06-20
> **TheHimself said:**
> I'd like to shrink the linux ext3 partition to make a new partition. When I run gparted using the Ubuntu (netbook remix) USB key, e2fsck does not give any errors but the command for shrinking keeps saying "Run e2fsck -f /dev/sda5 first." I don't know what's wrong.
So, what happens when you run  "e2fsck -f /dev/sda5"?

---

### Post by TheHimself on 2009-06-20
It doesn't give any errors or so, just one "large file".

---

