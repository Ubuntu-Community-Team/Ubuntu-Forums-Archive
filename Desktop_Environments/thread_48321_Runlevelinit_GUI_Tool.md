---
title: "Runlevel/init GUI Tool?"
date: 2005-07-12
forum: Desktop Environments
---

### Post by autocrosser on 2005-07-12
Just moved from YellowDog to Ubuntu & I would like to edit what is loading with runlevel 5---Yellowdog had a "control panel" that made it very easy to custom tune module loading--is anything similar available in Debian/Ubuntu?

Cheers!!
Dean

---

### Post by ubuntp on 2005-07-12
apt-get install bum

---

### Post by autocrosser on 2005-07-12
[QUOTE=ubuntp]apt-get install bum[/QUOTE]

Nice--now I can't get it with my source list--what repository is it?

---

### Post by psychicdragon on 2005-07-13
I don't think it's in any of the repos.
You can get it here: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by llamakc on 2005-07-13
```

[ken:etc](06:32 AM)$ cat inittab
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

```

Ubuntu boots into runlevel 2 by default. I was gonna write about /etc/init.d/ scripts and just removing gdm, yadda yadda, until I checked out that burn page. Very nice. Thanks for the link!

---

### Post by autocrosser on 2005-07-14
Got it--Thanks-was about what I was looking for---and it looks like it "persists"--checked after a reboot--still has my preferences without having to save it--


THANKS!!

Cheers!!
Dean :smile:

---

