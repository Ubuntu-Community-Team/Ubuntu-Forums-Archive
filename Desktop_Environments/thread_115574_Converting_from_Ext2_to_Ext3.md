---
title: "Converting from Ext2 to Ext3"
date: 2006-01-10
forum: Desktop Environments
---

### Post by ronmarley1 on 2006-01-10
When I first set up Ubuntu, I formatted the drive as Ext2 (it's what PartitionMagic suggested).  Should I convert my Ext2 file system to Ext3?  If it's a difficult process, is it worth it?  I'd hate to mess up what I have now (smooth running Windows free PC).
Thanks in advance...
Oops...  Maybe I should have posted this to Ubuntu 5.10 Support (GNOME) and not here.  I reposted in the correct forum.  Could a moderator please delete this entry?
Thanks again...  and sorry

---

### Post by Horndog on 2006-01-10
Try [this]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html") web site.

---

### Post by Suger on 2006-01-11
converting from ext2 to ext3 is as easy as
```
sudo tune2fs -j /dev/hdxy
```

replacing x and y with the proper letter and number.

---

