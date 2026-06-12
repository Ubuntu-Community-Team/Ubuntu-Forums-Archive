---
title: "How To use a Bug report?"
date: 2009-05-07
forum: General Help
---

### Post by ravi_buz on 2009-05-07
I have a problem with nautilus in 9.04 , and found that a bug report has been filed on it , so now how can i use that report to  solve the problem ,
Bug Report page=https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/335942

---

### Post by drs305 on 2009-05-07
ravi_buz,

From what I read in the bug reports, it has been fixed in the latest version of brasero. Since this hasn't made it's way into the main repositories, it is probably available for you in the jaunty proposed repositories.

To enable them, open Synaptic > Settings > Repositories: Updates. Tick "Unsupported updates (jaunty-backports)" then Close. Reload, then select the latest *brasero* package, which should contain the fix.

After you have made the update, you may want to go back and disable the "backports" repository.

---

