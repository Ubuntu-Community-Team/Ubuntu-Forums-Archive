---
title: "SDXC memory card"
date: 2010-10-12
forum: Desktop Environments
---

### Post by chejose on 2010-10-12
I have a new Panasonic camera that uses a SDXC memory card. Ubuntu does not see it, and from what I can see in Google it has a format that Ubuntu does not recognize.

But... there must be a driver or something to let Ubuntu know how to handle that format.

Can anyone help me with this?

Thanks,

José

---

### Post by DavePlummer on 2010-10-12
The SDXC specification requires use of the Microsoft exFAT file system. The Wikipedia article on exFAT ([http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)) contains a link to a beta version of a Fuse-based implementation. You will probably have to compile it and install it manually. I haven't tried it, so I can't comment on how well it works.

---

