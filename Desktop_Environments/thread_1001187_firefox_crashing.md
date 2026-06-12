---
title: "firefox crashing"
date: 2008-12-03
forum: Desktop Environments
---

### Post by Geran on 2008-12-03
Hi,

I'm recently having some firefox crashing issues. They come very often. I've tried rebooting. Whenever I try to run firefox from the terminal to get a glimpse at the error, it just outputs "Aborted.".

Any help?

thanks a lot,

G

---

### Post by Geran on 2008-12-03
Anyone? I think this is a common problem recently, but I haven't been able to find a good solution anywhere....

---

### Post by Geran on 2008-12-04
I'm sure there's a good way to do this with reinstalling...

---

### Post by Geran on 2008-12-04
can anyone point me to the solution?

---

### Post by Vantrax on 2008-12-04
try running it with strace in front

ie
strace firefox

should give you an idea where its crashing out.

---

### Post by Geran on 2008-12-05
When I run strace firefox I get this output repeated many times over.

read(15, 0x8e47964, 4096)               = -1 EAGAIN (Resource temporarily unavailable)
select(16, [15], [15], NULL, NULL)      = 1 (out [15])
writev(15, [{"\17\0\2\0\2\0\240\0", 8}], 1) = 8
select(16, [15], [], NULL, NULL)        = 1 (in [15])
read(15, "\1iC\1\0\0\0\0k\0\0\0\1\0\240\0\0\0\0\0\10\0\0\0\0\0\0"..., 4096) = 32


And it doesn't seem to end.

---

### Post by gb5757870 on 2008-12-05
Hey, just to confirm that I am getting very similar behaviour. Can't seem to place any pattern. Even after rebooting. 

Also ran the "strace firefox" and get the same as you do.

---

### Post by Geran on 2008-12-06
can we get any suggestions as to a solution?

---

### Post by drodiger on 2008-12-06
[http://ubuntuforums.org/showthread.php?t=1003357](http://ubuntuforums.org/showthread.php?t=1003357)

This is my post with the same problem and explanation of the problem (at least I think) :-)

---

### Post by gb5757870 on 2008-12-06
Thanks for letting us know the bug has been lodged. Hopefully it will be sorted out as driving me up the wall

---

