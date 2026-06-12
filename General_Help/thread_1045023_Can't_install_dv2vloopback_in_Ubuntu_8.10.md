---
title: "Can't install dv2vloopback in Ubuntu 8.10"
date: 2009-01-20
forum: General Help
---

### Post by New Horizon on 2009-01-20
Please forgive my ignorance in these matters.

I'm trying to install dv2vloopback so I can use my camcorder as a webcam, but the last version of dv2vloopback will not install.  When I run 'make' in the terminal, I get...

```
gcc -o dv2vloopback dv2vloopback.c -Wall -O3 --fast-math -lgd
dv2vloopback.c: In function ‘next_frame’:
dv2vloopback.c:104: warning: ignoring return value of ‘system’, declared with attribute warn_unused_result
dv2vloopback.c: In function ‘trapper’:
dv2vloopback.c:139: warning: ignoring return value of ‘system’, declared with attribute warn_unused_result
dv2vloopback.c:141: warning: ignoring return value of ‘system’, declared with attribute warn_unused_result
dv2vloopback.c: In function ‘main’:
dv2vloopback.c:176: warning: ignoring return value of ‘system’, declared with attribute warn_unused_result
strip dv2vloopback

```

I have no idea what any of that means, or how to fix it.  This is the equivalent of trying to read Chinese to me.

Getting this program running is the last step in getting my camera running.  Would appreciate any help.

---

### Post by New Horizon on 2009-01-20
I had no idea how busy these forums were when I signed up. :)  Wow.  Looks like a lot of people are using Ubuntu these days, that's great.  Sadly, I doubt I'll ever be a 'real' Linux user in the sense of understanding all the command line stuff, but I surely do love this OS.  Thanks to all involved.

Hope someone can help me with this issue.

---

### Post by New Horizon on 2009-01-20
Sorry, don't mean to be annoying.  Just really need some help with this.

---

