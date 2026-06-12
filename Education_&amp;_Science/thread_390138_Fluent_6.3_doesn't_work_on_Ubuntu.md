---
title: "Fluent 6.3 doesn't work on Ubuntu"
date: 2007-03-21
forum: Education &amp; Science
---

### Post by adas on 2007-03-21
I try run a [Fluent]("http://en.wikipedia.org/wiki/Fluent%2C_Inc.") on Ubuntu 7.04 (i think in 6.10 is the same problem).

When I run a ./fluent: 
```
EOF on stdout. The fluent process could not be started. 
```
And fluent doesn't work. (only fluent's terminal run).

When type: 
```
export LD_ASSUME_KERNEL=2.2.5 ./fluent 
```
in terminal I have a:
```
 /bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory 
```

And I don't know what i should do now... I created a symbolic links to libc.so.6 in some place... I have a libc6.

---

### Post by geirha on 2008-01-18
[http://ubuntuforums.org/showthread.php?t=407076](http://ubuntuforums.org/showthread.php?t=407076)

---

