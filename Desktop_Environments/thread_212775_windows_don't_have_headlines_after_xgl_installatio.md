---
title: "windows don't have headlines after xgl installation"
date: 2006-07-10
forum: Desktop Environments
---

### Post by berger1 on 2006-07-10
I installed xgl using exactly what this says:
[http://ubuntuforums.org/showthread.php?p=845077](http://ubuntuforums.org/showthread.php?p=845077)
and now my windows don't have headlines and I can't move them.

I followed the manual exactly without understanding what I'm doing

I have nvidia (can't remember exactly which) and kubuntu.

---

### Post by dan.imbrogno on 2006-07-10
hey i had the same problem after i installed XGL. Something went screwy with your installation. I can't offer any advice because i'm pretty new to linux, but i reinstalled ubuntu and tried again and it worked just fine.

Most likely some configuration you did as part of the process wasn't done correctly.

---

### Post by panurge77 on 2006-07-10
Something went wrong and compiz could not start. Run ```
compiz --replace gconf
``` and see what error you get

---

### Post by berger1 on 2006-07-10
doesn't work
"compiz.real: water: GL_ARB_fragment_program is missing"

---

### Post by konst88 on 2006-07-10
i had the same problem. then i used this guide: [http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)
after i downloaded all the packages which are related to XGL, it worked.

---

