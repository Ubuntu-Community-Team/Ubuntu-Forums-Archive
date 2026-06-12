---
title: "man: invalid option -- F"
date: 2006-02-23
forum: Desktop Environments
---

### Post by manx801 on 2006-02-23
Hello,

I am running Ubuntu 5.10.

When I try to read the man page for anything (tar, mount, cd, etc...) I get:

man: invalid option -- F
usage: man [-c|-f|-k|-w|-tZT device] [-i|-I] [-adlhu7V] [-Mpath] [-Ppager]
           [-Cfile] [-Slist] [-msystem] [-pstring] [-Llocale] [-eextension]
           [section] page ...
(I have cut out the rest of the help for brevity)


the binary I use to run man is:

/usr/lib/man-db/man

Any ideas as to how I might fix this?

Thanks.

---

### Post by lamego on 2006-02-23
Just reinstall man,
thats not the standard man path so something is really broken...
```
which man
/usr/bin/man
```

---

### Post by manx801 on 2006-02-23
Actually, I did try that and it had no effect.

/usr/bin/man is a symlink to /usr/lib/man-db/man

---

### Post by manx801 on 2006-02-23
Problem fixed. I found a function hidden in my old .bashrc file which was overloading man and passing the -F argument.

Thanks.

Paul

---

