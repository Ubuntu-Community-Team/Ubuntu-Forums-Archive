---
title: "broken dependencies by upgrading libc6"
date: 2005-09-29
forum: Desktop Environments
---

### Post by fantics on 2005-09-29
Hi. I was trying to install mysql on Breezy.

I read the following link and did the same thing :
[http://ubuntuforums.org/showthread.php?t=67944&highlight=mysql](http://ubuntuforums.org/showthread.php?t=67944&highlight=mysql)
As it said, I upgraded libc6, and that action made same problem that 'jalanbuntu' posted at the end on the same page. When I try to apt-get install, it shows the following error, and the console automatically crashes.
```

The following packages have unmet dependencies:
libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-22 is to be installed
libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-22 is to be installed
locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
I'm just a Linux beginner, so I hope I could get easy answer to understand.

Thanks.

---

### Post by mlomker on 2005-09-29
I added a post to the other thread.  I've been in this position before and learned the hard way that you never mess with lib6c.  It's a library used by almost every application on your system.  You may end up have to reload your machine, but good luck.

---

