---
title: "Privateer Remake on AMD64?"
date: 2006-06-09
forum: Gaming &amp; Leisure
---

### Post by Kemotaha on 2006-06-09
Anyone know how to install the privateer remake (the mod of Vegastrike) for AMD64?

I downloaded the .run file from their website but I keeping getting this error:

 error while loading shared libraries: libgdk-1.2.so.0: cannot open shared object file: No such file or directory

The file is there in /usr/lib/ so I think it is compaining that it is a 64 bit lib and it needs a 32-bit one.  Any ideas?

---

### Post by fr175 on 2006-09-09
> **Kemotaha said:**
> Anyone know how to install the privateer remake (the mod of Vegastrike) for AMD64?

I downloaded the .run file from their website but I keeping getting this error:

 error while loading shared libraries: libgdk-1.2.so.0: cannot open shared object file: No such file or directory

The file is there in /usr/lib/ so I think it is compaining that it is a 64 bit lib and it needs a 32-bit one.  Any ideas?

I am having the same issue.  Does anyone have a workaround?

---

### Post by fr175 on 2006-09-09
[THIS took care of the issue.](http://ubuntuforums.org/showthread.php?t=141392&highlight=libgdk-1.2.so.0)  It installs fine from there.

---

