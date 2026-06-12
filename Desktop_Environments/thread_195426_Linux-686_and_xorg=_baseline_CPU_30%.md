---
title: "Linux-686 and xorg= baseline CPU 30%"
date: 2006-06-12
forum: Desktop Environments
---

### Post by shuttleworthwannabe on 2006-06-12
I was following a thread during the dapper development period, and it was determined that linux-686 and xorg do not gel well: there was a memory leak and CPU usage was not optimized. It works well in linux-386 though. 

The reason I have installed the Linux-686 is because my machine is a 686, and have read that there are noticeable performance difference once a right kernel is installed. I do feel that apps open and close slightly faster, but not a whole lot faster.

Is the linux-686 and xorg "bug" fixed, or will it be? Any ideas on getting the xorg use less CPU at baseline (i.e. no applications running after bootup, and top, has xorg firing relentlessly). My base temperature readings in linux-383 are arounf 45-46'C; but in linux-686 they hoer around 48-51'C.

I wish there is a workaround for this.
Thanks,
swb

---

### Post by pyromithrandir on 2006-06-12
I saw a thread about this just the other day, so, I guess it isn't fixed.
Here's the bug report for it, I believe:
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570)

---

