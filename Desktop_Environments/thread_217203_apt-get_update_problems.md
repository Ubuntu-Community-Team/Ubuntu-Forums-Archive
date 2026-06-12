---
title: "apt-get update problems"
date: 2006-07-16
forum: Desktop Environments
---

### Post by sean_ on 2006-07-16
Hi, I'm trying to apt-get update, but it says this: ```
   1.
      Err http://packages.freecontrib.org dapper/free Packages
   2.
        404 Not Found
   3.
      Err http://packages.freecontrib.org dapper/non-free Packages
   4.
        404 Not Found
   5.
      Err http://packages.freecontrib.org dapper/free Sources
   6.
        404 Not Found
   7.
      Err http://packages.freecontrib.org dapper/non-free Sources
   8.
        404 Not Found
   9.
      Fetched 230kB in 16s (13.8kB/s)
  10.
      Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz 404 Not Found
  11.
      Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz  404 Not Found
  12.
      Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz  404 Not Found
  13.
      Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz  404 Not Found
  14.
      Reading package lists... Done
  15.
      W: Duplicate sources.list entry http://wine.budgetdedicated.com dapper/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_dapper_main_binary-i386_Packages)
  16.
      W: You may want to run apt-get update to correct these problems
  17.
      E: Some index files failed to download, they have been ignored, or old ones used instead. 

Raw Content Download: http://pastebin.ca/raw/89725
```

Can anybody help me?

---

### Post by jimmygoon on 2006-07-16
I've noticed the same thing.

---

### Post by tonym2 on 2006-07-16
I had the same problem. See the thread I started earlier today. I found a solution but can't "fully" test it yet. Running apt-get update shows no errors but I haven't tried to install anything that uses that repository yet..

[http://www.ubuntuforums.org/showthread.php?t=217050](http://www.ubuntuforums.org/showthread.php?t=217050)

---

