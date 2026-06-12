---
title: "connect to remote machine"
date: 2006-06-03
forum: Desktop Environments
---

### Post by tfmccull on 2006-06-03
How do i connect to a remote machine? Thunar does not yet have the capability to mount a remote file system. Help please!

---

### Post by taurus on 2006-06-03
Asssuming that you have sshd (ssh server) running on that machine, just connect to it with (from a terminal),
```

ssh -l your_username 123.45.67.89
(assuming that 123.45.67.89 is the IP address of that remote machine...)

```

---

### Post by tfmccull on 2006-06-05
should have been more specific. Is there a way to create a destop icon as a link to a remote share?

---

