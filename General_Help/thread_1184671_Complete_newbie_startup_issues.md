---
title: "Complete newbie: startup issues"
date: 2009-06-11
forum: General Help
---

### Post by h0rnguy on 2009-06-11
Everytime I try to log in to my recently installed copy of Ubuntu, instead of taking me to the desktop it asks for a login at the shell screen and keeps me in shell from that point on.  Does anyone have any idea what the problem may be?  Is there anything I can do to bring you all more information to solve the problem?  Any suggestions would be very appreciated!!

---

### Post by zvacet on 2009-06-11
After login in the shell type

```
startx
```

or 

```
sudo /etc/init.d/gdm start
```

If you get any errors post them here.

---

