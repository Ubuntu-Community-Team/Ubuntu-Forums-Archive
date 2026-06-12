---
title: "annoying request for Ubuntu CD"
date: 2005-12-31
forum: Desktop Environments
---

### Post by ernestorocks on 2005-12-31
I tried installing the new gaim 2.0 version, and basically, it didn't work out. it was kind of a mess, and i didn't really know what i was doing, and it kept requesting the Ubuntu CD. so i just stopped, and gaim 1.5 still works fine. but now, every time i want to install something in apt-get or synaptic, i get the same request for a CD and makes it almost impossible to install anything.


```
Please insert the disk labeled:
Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)
in drive /cdrom/
```

Does anyone know how to get rid of this?

Thanks.

---

### Post by earobinson on 2005-12-31
edit your /etc/apt/sources/list comment out the cd rom lines

EDIT

aka > deb cdrom:[Ubuntu 6.04 _dapper Badger_ - Alpha i386 (20050817)]/ dapper main restricted turns to > ## deb cdrom:[Ubuntu 6.04 _dapper Badger_ - Alpha i386 (20050817)]/ dapper main restricted


---

### Post by ernestorocks on 2005-12-31
o my god, thank you, haha you have no idea how annoying that was

---

