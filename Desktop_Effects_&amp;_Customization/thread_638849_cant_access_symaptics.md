---
title: "cant access symaptics"
date: 2007-12-12
forum: Desktop Effects &amp; Customization
---

### Post by dmsymr on 2007-12-12
I tried to install desktop screenlets via adding a new repository. Being new to ubuntu I find it easier using sudo apt-get rather than instal the tar. file The new repository didnt take and everytime i try to access synaptics now I get this message : 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

It means absolutely nothing to me, might as well be another language...I didnt have any luck googling it so im hoping it makes sense to anyone else. 
what on earth do I do?

DM:confused:

---

### Post by FuturePilot on 2007-12-12
Do this
```
sudo dpkg --configure -a
```

---

### Post by dmsymr on 2007-12-12
Seems to be doing the trick! Im learning every day, Merry Christmas!!

---

### Post by FuturePilot on 2007-12-12
You're welcome! ;)

---

