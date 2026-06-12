---
title: "Ksysguard and memory usage vs XFCE applet"
date: 2007-09-06
forum: Desktop Environments
---

### Post by krugman on 2007-09-06
Hello,

I have recently tried XFCE and overall, I like it. However, I have a question about memory usage. Under XFCE, I have an applet that monitors RAM abd CPU usage. For instance, now it says that I use 327 Mb out of 1002.
However, when I open Ksysguard it says that around 620000 Kb are used and that I only have 400000 Kb left.
Why the discrepancy?
Who is right?

Thanks!

---

### Post by GeneralZod on 2007-09-06
> **krugman said:**
> Hello,

I have recently tried XFCE and overall, I like it. However, I have a question about memory usage. Under XFCE, I have an applet that monitors RAM abd CPU usage. For instance, now it says that I use 327 Mb out of 1002.
However, when I open Ksysguard it says that around 620000 Kb are used and that I only have 400000 Kb left.
Why the discrepancy?
Who is right?


Both are "right", but XFCE's statistic is the more interesting one.  See e.g.

[http://ubuntuforums.org/showthread.php?t=490910](http://ubuntuforums.org/showthread.php?t=490910)

---

### Post by krugman on 2007-09-06
Oh, I see. I thought of something like that.
Thanks for the answer.
One last thing: do you know htop?
I have downloaded it and it says that I use 328 Mb which is what I expected with Thunderbird and Firefox open. But I am not sure I understand everything. For instance, where is the amount of RAM used by each program? Is it under RES? Then, why is there 8 instances of firefox with the same RES, MEM%...?

Thanks.

---

### Post by GeneralZod on 2007-09-06
> **krugman said:**
> Oh, I see. I thought of something like that.
Thanks for the answer.
One last thing: do you know htop?
I have downloaded it and it says that I use 328 Mb which is what I expected with Thunderbird and Firefox open. But I am not sure I understand everything. For instance, where is the amount of RAM used by each program? Is it under RES? Then, why is there 8 instances of firefox with the same RES, MEM%...?

Thanks.

I'm not familiar with htop, I'm afraid.  A decent approximation to an application's memory usage is given by subtracting SHR from RES, but it's all much more complex than that :)

---

