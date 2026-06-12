---
title: "Problem removing"
date: 2009-05-10
forum: General Help
---

### Post by RedSingularity on 2009-05-10
I just cant seem to remove a part of MythTV.  When i choose to Remove in package manager i get this crap,

```
E: mythtv-backend: subprocess pre-removal script returned error exit status 1
```


Any ideas?

---

### Post by Crafty Kisses on 2009-05-10
Try running these commands:
```
sudo /etc/init.d/mythtv-backend stop
sudo apt-get remove mythtv-backend
sudo apt-get update
```

---

### Post by RedSingularity on 2009-05-10
I get this when doing "stop"

* MythTV home directory, /home/mythtv does not exist.

---

### Post by RedSingularity on 2009-05-10
Do i need to reinstall mythtv and then try this again?

---

