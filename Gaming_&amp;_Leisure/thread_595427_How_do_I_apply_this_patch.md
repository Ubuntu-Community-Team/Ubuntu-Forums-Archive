---
title: "How do I apply this patch?"
date: 2007-10-28
forum: Gaming &amp; Leisure
---

### Post by DeafByPills on 2007-10-28
Well, I have that regression bug. I have the wine .48 source and there's a patch for it. It doesn't give instructions on hnow to implement this patch. Does anyone know?

It can be found at [http://bugs.winehq.org/show_bug.cgi?id=9878](http://bugs.winehq.org/show_bug.cgi?id=9878)

---

### Post by 5-HT on 2007-10-28
Same way you'd manually patch any source file...
From the top-level source directory: patch -Np1 < /path/to/patchfile
cheers,

---

### Post by DeafByPills on 2007-10-28
> **5-HT said:**
> Same way you'd manually patch any source file...
From the top-level source directory: patch -Np1 < /path/to/patchfile
cheers,


Dude, I owe you one.

Thanks a lot. I was trying to figure that one out for hours. I didn't know you could do that. :)

---

### Post by 5-HT on 2007-10-28
> **DeafByPills said:**
> Dude, I owe you one.

Thanks a lot. I was trying to figure that one out for hours. I didn't know you could do that. :)

Glad it worked :)

---

