---
title: "/tmp full with no files"
date: 2009-06-07
forum: Desktop Environments
---

### Post by shayfisher on 2009-06-07
Hello all,

I have a strange problem... /tmp gets full but when I try to find large files within it I cannot find. also storage space sum of all small files doesn't add up to the space of /tmp.
I've checked if something is locking files on /tmp - and didn't find nothing significant.
I've also checked the device file associated with /tmp - which resides on LVM and didn't find anything significant.

I've checked to see whether this is an Inodes problem - but something is weired - I get this output from df -i:
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/vg-tmp         0       0       0    -  /tmp

Do you know how to solve this thing ?
The computer gets stuck when /tmp gets full and it is really annoying.

Best regards,
shay.

---

