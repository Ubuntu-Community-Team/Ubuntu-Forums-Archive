---
title: "Strange problem w/ firefox and 2.6.27-7 kernel...."
date: 2008-10-26
forum: Desktop Environments
---

### Post by mbobak on 2008-10-26
Ok, this is really strange.  

I'm running 8.10, completely up-to-date as of today, on a Dell D630,
which has a BCM4312 (rev 01).

The default kernel for 8.10 is 2.6.27-7.  But, if I boot into 2.6.24-21,
everything works fine, I'm using it to write this post.  But, if I boot into 2.6.27-7, I can't surf the web!  That's NOT to say my network is broken.  I can 'ping google.com' successfully.  But, if I run firefox and enter 'google.com', firefox says "contacting google.com" and hangs indefinitely....  As soon as I boot back into 2.6.24-21, everything works fine again.

Some other salient facts:

In both cases, bcm43xx is blacklisted, and the kernel loads ssb &  b44.

When firefox is hanging, an strace reveals it looping very tightly and producing the following output:
```
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(19, "\372", 1)                     = 1
futex(0xac557c, 0x85 /* FUTEX_??? */, 1) = 1
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN}], 10, 0) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"5\30\4\0\325@\0\3\0\1\0\3\21\0\21\0\227\4\5\0\326@\0\3"..., 2092}], 1) = 2092
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN}], 10, 0) = 0
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(19, "\372", 1)                     = 1
futex(0xac557c, 0x85 /* FUTEX_??? */, 1) = 1
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN}], 10, 0) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"5\30\4\0\334@\0\3\0\1\0\3\21\0\21\0\227\4\5\0\335@\0\3"..., 2092}], 1) = 2092
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN}], 10, 0) = 0
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(19, "\372", 1)                     = 1
futex(0xac557c, 0x85 /* FUTEX_??? */, 1) = 1
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN}], 10, 0) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"5\30\4\0\343@\0\3\0\1\0\3\21\0\21\0\227\4\5\0\344@\0\3"..., 2092}], 1) = 2092
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=36, events=POLLIN}, {fd=19, events=POLLIN}], 10, 0) = 0
read(3, 0xa9e6f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll( <unfinished ...>
```

Anyone else seen something like this?  Not sure what 'EAGAIN' really means for a read() call.  

Any thoughts are appreciated.

Thanks,

-Mark

---

### Post by bburg on 2008-10-26
I have no network connection at all with my BCM4318. All worked fine in 8.04. If I boot with the same kernel as you (2.6.24-21) all is working. There must be something wrong with the latest kernel, I think.

---

### Post by mbobak on 2008-10-27
Hmm....thanks for the info.....I *hate* it when upgrading breaks existing functionality.  I was actually impressed w/ how seamlessly 8.04 saw my wireless card and used it.  I expected the same out of 8.10....

Foolish, I guess...

Anyhow, thanks for the info.

-Mark

---

### Post by mlissner on 2009-01-16
I found this thread because I am having a problem with futex wait calls in Firefox making the browser hang. You should pull up System Monitor, and see if Firefox is hanging on a Futex_wait. If so, that might be your answer...

---

