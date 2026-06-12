---
title: "Clock and calender suddenly gone from upper right corner 14.04LTS?"
date: 2014-12-22
forum: Desktop Environments
---

### Post by cybrsaylr on 2014-12-22
Boot up today and notice the clock, day of week and calender in missing in the top upper right hand corner?
How do I get it back?

---

### Post by CantankRus on 2014-12-22
Firstly try to reload unity by running...
```
**setsid unity**
```
or logging out and back in.

If still not showing try...
```
dconf write /com/canonical/indicator/datetime/show-clock true
```

---

### Post by cybrsaylr on 2014-12-22
CantankRus  Thanks.
> setsid unity
Did the trick! All is back to normal.

---

