---
title: "[SOLVED] Choppy image on debian etch"
date: 2008-06-29
forum: Debian
---

### Post by geo909 on 2008-06-29
Hello everybody.
 I have a somewhat old compaq presario 700 laptop.
I used the debian etch netinstall cd to do a minimal install. Then, I installed X and openbox to keep things light.

Anyway, almost everything is fine but I got a problem:

When I move/resize windows or scrolldown pages (firefox, editors etc)
I get some echo and the image is slow. It's really annoying after a while.

One thing I can guess is video drivers. I guess that doing a minimal install from the net CD makes debian use vesa. Is that the problem?
I have also set doublebuffer but that did not fix the problem.
Any ideas?

   Thanks a lot!


P.S My english are not very good. Do you understand what I mean by "choppy" and "echo"? Tell me if you need more info, I'll try my best to describe it.

---

### Post by tturrisi on 2008-06-29
boot to text login as root:
dpkg-reconfigure xserver-xorg

select the appropriate videon driver.

---

### Post by geo909 on 2008-06-29
Yes, that did the job.
Though it had a million other things to configure,
hope I didn't do any big mistakes!

Thanks a lot!

---

