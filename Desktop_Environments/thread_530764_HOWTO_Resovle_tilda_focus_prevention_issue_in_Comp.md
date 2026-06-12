---
title: "HOWTO: Resovle tilda focus prevention issue in Compiz Fusion"
date: 2007-08-20
forum: Desktop Environments
---

### Post by jupiter2006 on 2007-08-20
This seems to resolve the issue:
(for identifying a window in general you may find the following post helpful:
[http://forum.compiz-fusion.org/showthread.php?t=1768](http://forum.compiz-fusion.org/showthread.php?t=1768))

1- Open CompizConfig Settings Manager. For example, open a terminal and type:
```
ccsm
```

2- From the category pane select: 
General | General Options | Focus & Raise Behaviour

3- Find the "Focus Prevention Windows" attribute. The default value is "any", replace it with
```
any & !title=tilda
```

That's all!

---

### Post by dustigroove on 2007-08-24
Nice, that clears up one of the minor little usability nuisances that I had been living with since switching over to CF from Beryl.  Thanks.

---

### Post by cypresstwist on 2007-09-17
Thanks. Have been looking for a fix like this...

---

### Post by dustigroove on 2007-09-17
[FONT=Arial][SIZE=2][COLOR=Black]Actually a more appropriate entry might be:

```
any & !(title=^tilda$)
``` which would prevent any focus issues with other windows having tilda in the title (for instance firefox while you are reading this thread).

Cheers

.
[/COLOR][/SIZE][/FONT]

---

