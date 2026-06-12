---
title: "who glibc error"
date: 2006-02-28
forum: Desktop Environments
---

### Post by JeromeP on 2006-02-28
Hi Ubuntu community!

here is my problem:
jerome@jubuntu:~$ who
jerome   tty1         Feb 25 14:12
jerome   pts/0        Feb 26 21:42 (:0.0)
*** glibc detected *** free(): invalid pointer: 0x0804e900 ***
Abandon

I have Ubuntu 5.10
jerome@jubuntu:~$ uname -a
Linux jubuntu 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686 GNU/Linux

What's the problem doc?
Thank you

---

### Post by dcstar on 2006-02-28
[QUOTE=JeromeP]Hi Ubuntu community!

here is my problem:
jerome@jubuntu:~$ who
jerome   tty1         Feb 25 14:12
jerome   pts/0        Feb 26 21:42 (:0.0)
*** glibc detected *** free(): invalid pointer: 0x0804e900 ***
Abandon

I have Ubuntu 5.10
jerome@jubuntu:~$ uname -a
Linux jubuntu 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686 GNU/Linux

What's the problem doc?
Thank you[/QUOTE]
Don't really know, but I'd be upgrading to the 686 kernel version just to see if it makes any difference.

---

### Post by JeromeP on 2006-03-02
I'll try this!
Thanks

---

### Post by JeromeP on 2006-03-05
Ok, kernel for 686 fixed it!
Thanks!

---

