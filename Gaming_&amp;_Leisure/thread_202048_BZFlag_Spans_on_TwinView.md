---
title: "BZFlag Spans on TwinView"
date: 2006-06-22
forum: Gaming &amp; Leisure
---

### Post by Kratos on 2006-06-22
I'm using the version of BZFlag from the repos, and I have TwinView enabled on my nVidia GeForce 6200. When I try to play BZFlag, it spans across both monitors. How can I confine it to my primary monitor? .conf mashing? Any help would be greatly appreciated. 

Thanks in advance,

Kratos

---

### Post by robdor on 2006-06-27
I believe that you just have to make a meta mode that blanks out the second monitor for whatever resolution you use for BZFlag.

Kind of like this:
800x600, NULL;

I could be wrong here, it's just a guess...

---

### Post by Skye on 2006-06-28
I had the same problem, but I fixed it by running bzflag with these arguments:
```
bzflag -geometry 1280x1024 -window
```
That assumes you have a monitor with a 1280 x 1024 resolution- if yours is different, just change it.

---

### Post by Kratos on 2006-06-28
Thanks, that's exactly what I needed. :)

---

