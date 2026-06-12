---
title: "dpkg name error"
date: 2006-07-02
forum: Desktop Environments
---

### Post by kf4ypd on 2006-07-02
when i try to use either apt-get or synaptic to install a package, i get the following error

```
Fetched 136kB in 1s (68.6kB/s)
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 19:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
```


i tried looking in the file near line 19, and it appeared normal.
but this makes my apt-get entirely useless, any suggestions?

**EDIT: problem solved[B]**[/B] i was screwing around in dselect, and something i did in there fixed it

---

### Post by Lycaon on 2006-07-02
I dont have a clue myself but, did you try to sudo apt-get update? (and mayb upgrade)

---

### Post by kf4ypd on 2006-07-02
yes, i tried update, clean, upgrade
update and clean both finish succesfully, but problem still exists when installing

also tried deleting the file that the error points to, then updating, still no luck

---

