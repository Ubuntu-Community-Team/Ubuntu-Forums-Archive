---
title: "dpkg probs, can't install anything..."
date: 2005-04-25
forum: Desktop Environments
---

### Post by yanik on 2005-04-25
This is what I get whenever I try to install somthing thru apt-get.  I tried apt-get -f install and it didn't change anything.  I'm not very familiar with dpkg, other than dpkg -i .

```
Preconfiguring packages ...
dpkg: syntax error: unknown group `fuse' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Any help would be great, 

Thanks

Yanik

---

### Post by hobnob on 2005-04-25
Unfortunately there is a bug in the fuse uninstall procedure which does not do all the necessary housekeeping. I'm guessing you installed fuse and then removed it at a later date, and are now left with this error. Until the package is fixed, there is a quick workaround that should get apt working again -- you just need to manually add the group 'fuse' with ```
$ sudo groupadd fuse
```

---

### Post by yanik on 2005-04-25
cool, it worked.

thanks hobnob

---

### Post by chinaski on 2005-11-10
yes, thanks a lot! ;)

---

