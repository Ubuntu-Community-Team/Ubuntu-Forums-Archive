---
title: "yet Another HIbernate Problem"
date: 2009-06-13
forum: General Help
---

### Post by me.translucent on 2009-06-13
Help can not Hibernate :(

---

### Post by PGScooter on 2009-06-13
have a looky here:

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by me.translucent on 2009-06-16
whenever i hibernate(normal method) it tries to hibernate but then in a blank screen it says can't find the swap device try swap on -a my swapon -s output is 
```

Filename				Type		Size	Used	Priority
/dev/sda8                               partition	2128572	0	1


```

---

### Post by utnubuuser on 2009-06-16
you've got 2gigs of swap space.  how much ram is installed?

---

### Post by me.translucent on 2009-06-16
2 gigs

---

### Post by utnubuuser on 2009-06-24
sorry to not get back to you in a timely fashion...

Have you tried alocating a little more swap space? - I was under the impression that one had to have slightly more swap than ram for hybernate/suspend to ram function properly.

---

