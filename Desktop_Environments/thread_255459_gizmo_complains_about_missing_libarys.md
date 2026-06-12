---
title: "gizmo complains about missing libarys"
date: 2006-09-11
forum: Desktop Environments
---

### Post by sharperguy on 2006-09-11
```
gizmo: error while loading shared libraries: libdns_sd.so: cannot open shared object file: No such file or directory
```

But there may be other librarys

I got it from the gizmo website (the deb), the need to add more dependancies i think.

It should be in repos also

---

### Post by Dinerty on 2006-09-11
Did you install all 3 Gizmo project debs the correct way?. 
This is the order the deb's are supposed to be installed in.

1. bonjour
2. libsipphoneapi
3. gizmo-project

---

### Post by sharperguy on 2006-09-11
ok cheers, works now

I should have clicked "installation help"

but as a former windows user, "help" still translates as

"If you click this you going to get a big list of crap which you already tried because its just comon sence, but you can phone our support line a £2 a minuate, so you can talk to an indian who tells you to do the same things that this page just told you to do"

edit: still like to see a repo of this at some point though

---

### Post by chandra on 2006-09-19
See 

[http://www.ubuntuforums.org/showthread.php?p=1517267#post1517267](http://www.ubuntuforums.org/showthread.php?p=1517267#post1517267)

in case it helps.

---

