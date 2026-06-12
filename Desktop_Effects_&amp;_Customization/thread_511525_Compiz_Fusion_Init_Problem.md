---
title: "Compiz Fusion Init Problem"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by damir_1105 on 2007-07-27
I have installed compiz fusion and all work fine. Because is compiz is still in development state, updates are available daily. Two days ago i install update and now Compiz Fusion woun't start. Sorry for bad English. This is the problem:

```
damir@linux:~/src/madwifi-ng-r2619-20070727$ compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070707 and actual version is 20070708
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
```

---

### Post by keck on 2007-07-28
Getting same issue:

> compiz --replace -c emerald

/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070707 and actual version is 20070708
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

There was an update in the repo last night, and this happened; another update this AM and no change from my perspective :) 

How do we contact the package maintainer?

---

### Post by lennartack on 2007-09-24
Wich repositories do you guys use for compiz fusion, and do you have feisty or gutsy?

---

