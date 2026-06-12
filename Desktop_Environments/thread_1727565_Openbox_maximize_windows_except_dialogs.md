---
title: "Openbox: maximize windows except dialogs"
date: 2011-04-12
forum: Desktop Environments
---

### Post by decomp on 2011-04-12
Hello!

I have configured openbox to maximize all windows except dialog boxes but it maximizes them anyway.

I have edited my openbox rc.xml to maximize all windows like this:
```
<application class="*">
<maximized>yes</maximized>
</application>
```
This works fine but it also maximizes dialogs. So I added another rule:
```
<application type="dialog">
<maximized>no</maximized>
</application>
```

But the second rule doesn't work. any ideas?

I got these ideas from looking at [http://openbox.org/wiki/Help:Applications](http://openbox.org/wiki/Help:Applications) and [https://bbs.archlinux.org/viewtopic.php?id=94082](https://bbs.archlinux.org/viewtopic.php?id=94082)
I am using openbox inside and lxde session. This is not lubuntu; I installed openbox/lxde from the repos.

---

### Post by decomp on 2011-04-13
bump

---

### Post by decomp on 2012-05-31
A year later and I'm still wondering how to solve this..

---

### Post by drink on 2012-09-07
> **decomp said:**
> A year later and I'm still wondering how to solve this..

use type=normal and then you don't need an exclusion

---

