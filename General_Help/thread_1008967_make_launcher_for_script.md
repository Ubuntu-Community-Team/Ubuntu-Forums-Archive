---
title: "make launcher for script"
date: 2008-12-12
forum: General Help
---

### Post by bravemenrun333 on 2008-12-12
hello, i have the following script "aptana" that i want to execute with a launcher in my panel. until now, i always had to do it by terminal, by entering "sh aptana". please help me with this banal problem :confused:

script:
```
export MOZILLA_FIVE_HOME=/usr/lib/xulrunner
/usr/local/aptana/AptanaStudio
```

---

### Post by sdennie on 2008-12-12
Try making your launcher:

```

sh -c "MOZILLA_FIVE_HOME=/usr/lib/xulrunner /usr/local/aptana/AptanaStudio"

```

---

