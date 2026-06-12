---
title: "Funny attributes with ls"
date: 2009-02-18
forum: General Help
---

### Post by Isambard Mews on 2009-02-18
I have a directory with attributes:

drwxr-xr-T

What does the last capital T mean? Is there a reference for this stuff?

---

### Post by mikewu on 2009-02-18
The T replaces the execute bit. It means that the user can only delete or modify the files in the directory that they own or have write permission for.

---

### Post by bodhi.zazen on 2009-02-18
Those symbols are "sticky bits"

> If the sticky-bit is set on a file or directory without the execution bit set for the *others* category (non-user-owner and non-group-owner), it is indicated with a capital **T**:

See :

[http://unixfoo.blogspot.com/2008/01/sticky-bit.html](http://unixfoo.blogspot.com/2008/01/sticky-bit.html)

[http://www.zzee.com/solutions/unix-permissions.shtml#setuid](http://www.zzee.com/solutions/unix-permissions.shtml#setuid)

[http://www.codecoffee.com/tipsforlinux/articles/028.html](http://www.codecoffee.com/tipsforlinux/articles/028.html)

[http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)

---

