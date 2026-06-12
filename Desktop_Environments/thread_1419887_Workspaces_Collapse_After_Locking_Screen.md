---
title: "Workspaces Collapse After Locking Screen"
date: 2010-03-02
forum: Desktop Environments
---

### Post by evanrooney on 2010-03-02
Hi All,
This is my first post, I'll try to explain the issue the best I can. I'm running Ubuntu 9.10 and this problem occurs maybe once every 50 screen locks, which isn't too often but often enough that it's becoming very annoying. I work on 6 workspaces at a time and after unlocking my screen I find that all my workspaces have collapsed to one workspace, desk 1 to be exact. Does anyone know why this happens? Is there a fix for this?
Thanks in advance,
Evan

---

### Post by chewearn on 2010-03-02
When the workspaces "collapsed", does it mean you have one workspace left?  Or does it mean all your opened applications moved to desk1, but you still have six workspaces?

If it's the latter, it could be compiz has crashed.  Do you still see any desktop effects? E.g. the animations when opening/closing, or minimising?

If compiz has crashed, try press ALT+F2, enter "compiz --replace" into the box.  This should restart compiz and restore the applications back to the prior workspaces.

---

