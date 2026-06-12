---
title: "Compiz Problems 12.10"
date: 2012-10-28
forum: Desktop Environments
---

### Post by columbo1977 on 2012-10-28
Hey All

I upgraded last night to 12.10 and now my Compiz is all messed up.....

When I zoom out to see the cube my windows are all over the place?

Any idea how to get this sorted?

Thanks

Graham

---

### Post by zombifier25 on 2012-10-28
Upgrading may have messed up your config. Use this command to reset all Compiz settings:
```
gconftool --recursive-unset /apps/compiz-1
```

---

### Post by grahammechanical on 2012-10-28
You will also notice that the Compiz Configuration Settings Manager has been modified. So, before you ask, please read this:

[http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/]("http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/")

Regards.

---

