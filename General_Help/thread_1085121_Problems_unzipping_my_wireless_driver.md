---
title: "Problems unzipping my wireless driver"
date: 2009-03-02
forum: General Help
---

### Post by ___DEL___ on 2009-03-02
when i attempt to install a wireless driver i get this kinda problem, are there any ideas as to why?

```
richard@richard-laptop:~$ tar zxvf madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
tar: madwifi-hal-0.10.5.6-r3942-20090205.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting no
tar:Child returned status 2
tar: Error exit delayed from previous errors
```

---

### Post by Crafty Kisses on 2009-03-02
It could be a number of things. I'm guessing it's probably a permission issue, try putting "sudo" in front of the command and see if that makes a difference.

---

### Post by ___DEL___ on 2009-03-02
I just tried sudo and got the error again.  And the file is in the correct directory.

---

