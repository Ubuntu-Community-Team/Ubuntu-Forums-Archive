---
title: "Buggy Beryl"
date: 2006-10-30
forum: Desktop Environments
---

### Post by whoosh on 2006-10-30
So when Beryl-manager runs at startup, the toolbars on all my windows kinda do a thing where they flash.  You can't really drag the windows either. 

When you close the little beryl-diamond thingie in the panel, the problem goes away and I still get 3d effects.  It's not too big of a deal, just wondering if there was anyway I could fix it.

---

### Post by stenka on 2006-10-30
I am having the same problem since the last upgrade.

You can fix it by this way :
```
# sudo killall gtk-window-decorator
```

Then, reload the decorator manager using the menu of Beryl.

---

### Post by SishGupta on 2006-10-30
I also have this problem. I can tell when it will occur because beryl take significantly longer to start when it happens.

I can work around it but its frustrating as it makes it impossible to have beryl start with ubuntu.

---

### Post by ronmarley1 on 2006-10-30
This is a known issue.  You can read about it in many posts at [http://forum.beryl-project.org/index.html](http://forum.beryl-project.org/index.html).  My solution was to add "emerald" to startup programs.  Others suggest adding "emerald --replace". Give that a try and see what happens.

---

