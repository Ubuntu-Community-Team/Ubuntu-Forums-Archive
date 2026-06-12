---
title: "Expect script help"
date: 2009-05-09
forum: General Help
---

### Post by kenpotf on 2009-05-09
All,

I have a test script:

#!/usr/bin/expect -f
spawn date

All this does is print "spawn date". When I run the same command from expect's cli, I get the same thing. Is there another dependency that I'm missing?

All I installed was expect: apt-get install expect

Thanks,
John

---

### Post by kenpotf on 2009-05-09
Never mind. Apparently, it also expects a response instead of just launching a connection.

Thanks,

---

