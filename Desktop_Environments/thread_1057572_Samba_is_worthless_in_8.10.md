---
title: "Samba is worthless in 8.10"
date: 2009-02-01
forum: Desktop Environments
---

### Post by georger on 2009-02-01
Well, apparently this may be an old bug, but it makes Ubuntu completely worthless to me. [https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-April/001367.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-April/001367.html) describes my situation, as I NEED software and files that reside on a samba server, and the inability to connect to a samba server with plaintext passwords (read: a samba server with over 1k users) means that i've got to remove ubuntu. Attached is my smb.conf, with plaintext passwords enabled via the client plaintext auth = yes line in the configuration, but samba in ubuntu has a lack of plaintext passwords hardwired in. Please e-mail me if you have another solution, although I am certain my configuration is correct.

---

### Post by nikgare on 2009-02-02
This is from the link you quoted above:
> Marking as 'invalid'.  If you find that you're still having problems,
feel free to reopen the bug by setting the status back to 'new' and
giving more info.

Have you reopened the bug, or followed the solution/workaround?

---

