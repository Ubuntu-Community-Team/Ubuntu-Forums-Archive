---
title: "binutils upgrade"
date: 2005-05-27
forum: Desktop Environments
---

### Post by hunham on 2005-05-27
Hi,
After the latest binutils upgrade, I can't seem to be able to link my code any more. I keep getting:

/usr/lib/gcc/i486-linux/3.4.4/../../../../lib/crt1.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status

Maybe libc6-dev should also have been part of the upgrade?
Thanks,
--Gabor

---

### Post by alastair on 2005-05-27
I thought - "binutils" upgrade? Then I saw it.

But, as a test, before I upgraded I tested a compile/link of a simple "hello world" C program. OK.

I then upgraded and tried the compile/link again - and it is still OK.

So .... more detail (and a test program perhaps).

---

### Post by alastair on 2005-05-27
OK - you perhaps need to update again - see the security announcements. It appears binutils was  slightly broken :

[http://www.ubuntuforums.org/forumdisplay.php?f=17](http://www.ubuntuforums.org/forumdisplay.php?f=17)

---

### Post by hunham on 2005-05-27
Thanks that did it. Ubuntu is the best!

---

