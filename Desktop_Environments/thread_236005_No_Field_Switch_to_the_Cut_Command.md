---
title: "No Field Switch to the Cut Command?"
date: 2006-08-14
forum: Desktop Environments
---

### Post by jackn on 2006-08-14
Is sth wrong with the -f swich to the 'cut' command or is it me?!

```
:~/experimental$ ls -l
total 12
-rwxr--r-- 1 jackn jackn 86 Aug 13 23:59 garrels-script
-rwxr-xr-x 1 jackn jackn 42 Aug  4 23:04 test.del
-rwxr-xr-x 1 jackn jackn 22 Aug 12 23:53 test2
:~/experimental$ ls -l|cut -f 5
total 12
-rwxr--r-- 1 jackn jackn 86 Aug 13 23:59 garrels-script
-rwxr-xr-x 1 jackn jackn 42 Aug  4 23:04 test.del
-rwxr-xr-x 1 jackn jackn 22 Aug 12 23:53 test2
:~/experimental$ ls -l|cut -f 1-3
total 12
-rwxr--r-- 1 jackn jackn 86 Aug 13 23:59 garrels-script
-rwxr-xr-x 1 jackn jackn 42 Aug  4 23:04 test.del
-rwxr-xr-x 1 jackn jackn 22 Aug 12 23:53 test2
```

Output with or without the 'cut' command is identical. Can't get -f to pick out only the listed field(s). 

The -b swich, on the other hand, works just fine:

```
:~/experimental$ ls -l|cut -b 1-10
total 12
-rwxr--r--
-rwxr-xr-x
-rwxr-xr-x
```

?...
Thanks.

Jackn

---

### Post by Jussi Kukkonen on 2006-08-14
You'll need to use -d to set delimiter char -- but it probably still won't work right (cut is not very sophisticated). I suggest using awk. Try something like:
```
 ls -l | awk '{print $6 $7}'
```

---

### Post by jackn on 2006-08-14
OK. 
With -d switch:

```
:~$ ls experimental
garrels-script  test.del  test2
:~$ ls -l experimental/  | cut -f 1,3 -d" "
total
-rwxr--r-- jackn
-rwxr-xr-x jackn
-rwxr-xr-x jackn

```

With 'awk':

```
:~/experimental$ ls -l | awk '{print $3 ":" $9}'
:
jackn:garrels-script
jackn:test.del
jackn:test2

```

Will study 'awk' further.

What a quick, knowledgeable response. Nice to be talking the same language, so to speak.

Grateful,
Jackn

---

