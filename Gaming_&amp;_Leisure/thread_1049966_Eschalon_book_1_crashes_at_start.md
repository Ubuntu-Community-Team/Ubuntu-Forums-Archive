---
title: "Eschalon book 1 crashes at start"
date: 2009-01-25
forum: Gaming &amp; Leisure
---

### Post by Axx83 on 2009-01-25
I have ubuntu 8.10 with Intel 945 graphics, here's what it says when I try to run the game:
```
USER@USER-laptop:~/eschalon_book_1_demo$ ./eschalon_book_1_demo
Setting sound driver: Default
eschalon_book_1_demo: ../common/dri_bufmgr_fake.c:576: dri_bufmgr_fake_contended_lock_take: Assertion `((&bufmgr_fake->on_hardware)->next == (&bufmgr_fake->on_hardware))' failed.
Aborted

```
same with the complete version.

There's a post on the official board but no solution so far:
[http://basiliskgames.com/forums/viewtopic.php?f=11&t=1951&start=0]("http://basiliskgames.com/forums/viewtopic.php?f=11&t=1951&start=0")

Did someone solve this problem ?

---

### Post by Axx83 on 2009-01-26
I filed a bug, if anyone is interested:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/321401]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/321401")

---

