---
title: "Xorg nepomuk and virtuos take most of the cpu"
date: 2010-05-29
forum: Desktop Environments
---

### Post by kirys on 2010-05-29
Virtuoso neopomunk and xorg take most of the cpu while on indexing


```
 1429 root      20   0  294m  96m  22m R   44  4.9  36:25.55 Xorg                                                                                                                                              
 1880 kirys     39  19  530m  47m  20m S   44  2.4  12:50.73 nepomukservices                                                                                                                                   
 1786 kirys     20   0  138m  45m 3336 S   30  2.3  15:39.85 virtuoso-t
```

I can understand the complexity of the indexing but the cpu usage of xorg means to me that there is a lot of unnecessary refesh on the interface during the process even if there is no open dialog.

Cya

---

### Post by shaka_zulu on 2010-05-29
From my experience it will take some time until it index everything but after that you will not notice it. When i say some time i mean half an hour or even whole hour. Depends on number and complexity of your files.

---

### Post by shaka_zulu on 2010-05-29
Not to forget, try to limit Nepomuk on just a few folders and not all of them on all partitions. That will significantly reduce indexing time.

---

