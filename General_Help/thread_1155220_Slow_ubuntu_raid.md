---
title: "Slow ubuntu raid"
date: 2009-05-10
forum: General Help
---

### Post by jernejk on 2009-05-10
Hi,

I have a server with ubuntu 8.04 and raid 1 (md); disk read and writes, however, are quite slow.

This is bonnie++ report for my server:
Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
hal      48280M 29266  49 42015  12 15601   3 20186  29 30907   2  74.7   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
hal,48280M,29266,49,42015,12,15601,3,20186,29,30907,2,74.7,0,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++


For comparison, this is bonnie result on my laptop with quite slow disk:
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
laptop    8G 33406  58 42894  23 21887  11 49521  84 43981  11 131.7   1
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 17923  36 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
laptop,8G,33406,58,42894,23,21887,11,49521,84,43981,11,131.7,1,16,17923,36,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++

Any ideas?

---

### Post by danwood76 on 2009-05-10
I cant read the output!
Enclose it in code tags and it should format it better.

The best way to test disk throughput is with hdparm:
```

sudo hdparm -t /dev/DISK

```
Could you report the read speeds from that command please?

---

