---
title: "computer won't let me get java"
date: 2006-09-12
forum: Desktop Environments
---

### Post by blackdalek on 2006-09-12
I'm trying to install java onto a 1.2G AMD Duron machine. For some reason when I go to tick the sun-java5-bin to install it I get this...

"'sun-java5-bin' is not available in any software channel
The application might not support your system architecture."

What's up with that?

---

### Post by statue on 2006-09-12
AMD Duron is 64bit isn't it? If so thats why, java isnt made for 64 bit linux. Flash/shockwave aren't either.

---

### Post by blackdalek on 2006-09-13
> **statue said:**
> AMD Duron is 64bit isn't it? If so thats why, java isnt made for 64 bit linux. Flash/shockwave aren't either.

No, it's 32bit. Apparently I just needed to edit the sources.list file and add multiverse. Now it lets me install.

---

