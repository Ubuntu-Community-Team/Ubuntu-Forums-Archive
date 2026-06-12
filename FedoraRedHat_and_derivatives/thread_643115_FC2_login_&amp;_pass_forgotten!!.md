---
title: "FC2 login &amp; pass forgotten!!"
date: 2007-12-17
forum: Fedora/RedHat and derivatives
---

### Post by NotoriousTF on 2007-12-17
Hey,
A friend of mine is having a problem with Fedora Core II, personally I'm a Ubuntu user so I've no help to offer her. I told her I'd post here, to see if someone can help us out.
So she installed FC2 over two years ago and she has forgotten her username and password. Now supposedly there are default's but any default usernames found on-line haven't worked yet. Any one have any ideas on how to sort this out?

Thanks!

---

### Post by jinx099 on 2007-12-17
There is no "default" password for FC2 AFAIK.  Just boot it up into single user mode (append a 1 to the end of the boot line in grub) and then when it boots up, you should have root access.  Then just run "passwd" to change root's password.  From there you can reboot and log in normally as root and then see the other users and change their passwords too.

---

