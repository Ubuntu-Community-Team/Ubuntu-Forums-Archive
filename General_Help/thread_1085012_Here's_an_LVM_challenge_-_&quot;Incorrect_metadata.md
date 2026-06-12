---
title: "Here's an LVM challenge - &quot;Incorrect metadata area header checksum&quot;"
date: 2009-03-02
forum: General Help
---

### Post by MountainX on 2009-03-02
My USB flash drive is giving me this message when I run vgsan:

  Incorrect metadata area header checksum
      /dev/sdg: size is 3905536 sectors
      /dev/sdg1: size is 3905504 sectors
      /dev/sdg1: size is 3905504 sectors
      /dev/sdg1: No label detected

How do I fix this? 

I tried to exclude it by editing /etc/lvm/lvm.conf :
```
filter = [ "r|/dev/sdg|" ]
```

when I reran vgscan, the result was the same. I want to remove this message because I'm getting ready to start screwing with my LVs and I want to start clean.

---

