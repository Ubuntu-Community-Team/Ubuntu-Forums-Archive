---
title: "Getting a file not exists error despite file existing"
date: 2009-03-04
forum: General Help
---

### Post by BenedekHere on 2009-03-04
Here's a copy from the console:
```
/media/Data/linux/gamess$ ls -l
total 17696
drwxrwxrwx 1 root root        0 2009-03-03 22:42 dat
-rwxrwxrwx 1 root root    30786 2008-04-28 14:51 ddikick.x
-rwxrwxrwx 1 root root   585748 2007-07-12 06:37 ericfmt.dat
-rwxrwxrwx 1 root root 17418115 2008-04-28 14:50 gamess.Apr112008R1.x
-rwxrwxrwx 1 root root     1981 2008-04-28 14:51 gms
drwxrwxrwx 1 root root        0 2008-04-28 14:54 mcpdata
-rwxrwxrwx 1 root root     1145 2007-07-12 06:37 README
-rwxrwxrwx 1 root root    10231 2009-03-03 23:27 run
-rwxrwxrwx 1 root root    10254 2009-03-03 23:27 run~
-rwxrwxrwx 1 root root    33171 2008-04-28 14:51 rungms
drwxrwxrwx 1 root root        0 2009-03-03 23:47 scr
drwxrwxrwx 1 root root     8192 2008-04-28 14:53 tests
/media/Data/linux/gamess$ ./ddikick.x
bash: ./ddikick.x: No such file or directory

```
I can run "./gamess.Apr112008R1.x"
So this isn't some generic problem with the entire directory permissions or something.

What is going on!?
I'm new to linux and these kinds of things confuse the hell out of me.

---

