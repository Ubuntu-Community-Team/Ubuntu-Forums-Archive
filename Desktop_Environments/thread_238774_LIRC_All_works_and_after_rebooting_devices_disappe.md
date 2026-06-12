---
title: "LIRC: All works and after rebooting devices disappear..."
date: 2006-08-18
forum: Desktop Environments
---

### Post by hexion on 2006-08-18
Hi!

I have a problem with LIRC. I followed the instructions at this [page]("http://rubensa.wordpress.com/2006/05/24/ubuntu-lirc/") and everything worked.

But, after rebooting, /dev/lirc is no more there.

The only way to make things work again is going to /usr/src/lirc-0.8.0 and doing a make install again.

I made a "fix" to solve this problem:

I edited /etc/rc.local and added these lines:
> cd /usr/src/lirc-0.8.0/
make install
chmod 666 /dev/lircd
lircd


This way, everytime I boot it compiles and installs lirc. It works, but I hope there's a better way to make this work.

Any help?
Thanks in advance.

---

### Post by hexion on 2006-08-18
I found it!

My new /etc/rc.local (just lirc related lines) is:
> mknod /dev/lirc c 61 0
lircd

Now it works everytime I boot.

---

### Post by wiz561 on 2006-09-04
Oh my god....thank you ****SOOOOOO**** much for posting your fix.  I've been struggling with this now for the past day.  

Thank you again!

Mike

---

### Post by hexion on 2006-09-07
You're wellcome :)

---

