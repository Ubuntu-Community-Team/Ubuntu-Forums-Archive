---
title: "Shows 0 bytes free but there are 4 GBs free!"
date: 2010-12-27
forum: Desktop Environments
---

### Post by El Potro on 2010-12-27
Hi everyone,

After a long time, I'm back into Ubuntu.

The story goes like this: my partition /docs says it has 0 bytes free. But that isn't real. If has more than 4 GBs free!

```
mauri@bestia:~$ df
&#1060;&#1072;&#1081;&#1083;&#1086;&#1074;&#1072;&#1103; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;           1K-&#1073;&#1083;&#1086;&#1082;&#1086;&#1074; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1086;, &#1056;&#1072;&#1079;&#1088;&#1077;&#1096;&#1077;&#1085;&#1086; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1100;% &#1089;&#1084;&#1086;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1072; &#1085;&#1072;
/dev/sda2             20184676   2704964  16454364  15% /
none                    504236       328    503908   1% /dev
none                    508456       464    507992   1% /dev/shm
none                    508456       112    508344   1% /var/run
none                    508456         0    508456   0% /var/lock
none                    508456         0    508456   0% /lib/init/rw
none                  20184676   2704964  16454364  15% /var/lib/ureadahead/debugfs
/dev/sda1                93307     24143     64347  28% /boot
/dev/sda6            116881140 112317452         0 100% /docs
/dev/sda5             19228276  16078708   2172820  89% /home
/dev/sdb5             56894164  55733868   1160296  98% /media/WIN
```

What's going on here??

Thank you all in advance

---

### Post by bryanl on 2010-12-27
the system will reserve 5% by default in case there are any log files or such on the partition that need to be written when otherwise the partition is full. tune2fs manages this - check the man page.

use 'sudo tune2fs -l /dev/sda6' and look for how many blocks have been reserved.

If you are sure you don't need any system reserve on the drive, use 'sudo tune2fs -m 0 /dev/sda6' to remove the reserve allocation and free up the space.

as always, usual caveats apply. standard disclaimers as well. 

**This is a common question.** It took me a coon's age to find out about this reserved space. With large partitions, the reserve can really add up. It appears to be generally safe to remove to reserve allocation on a drive used for data storage only.

---

### Post by El Potro on 2010-12-27
Problem Solved, thank you very much **bryanl**.:popcorn:

---

