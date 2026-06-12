---
title: "LANG issues?"
date: 2005-10-17
forum: Gaming &amp; Leisure
---

### Post by Mirth on 2005-10-17
Output:

```
mirth@ubuntu:~$ cedega /home/mirth/SEGA/PhantasyStarOnline/online.exe LANG=en_USFor language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
```

How do I specify what language to run it in, because I'm most likely sure that this is the only issue that's keeping me from running PSO now.  The drivers work, thanks to you guys earlier =).

---

### Post by seethru on 2005-10-17
export LANG=en_US
then in the same terminal run the game.

---

### Post by Mirth on 2005-10-17
No go.  I tried the other LANGs that were available as well.

```
mirth@ubuntu:~$ export LANG=en_US
mirth@ubuntu:~$ cedega /home/mirth/SEGA/PhantasyStarOnline/online.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
```

---

