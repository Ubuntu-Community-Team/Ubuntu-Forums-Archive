---
title: "Gnome-panel trouble"
date: 2006-04-07
forum: Desktop Environments
---

### Post by æþeling on 2006-04-07
When I start a gnome session, a message pops up, saying gnome-panel has encountered an error and crashed. If I click restart or close the same message pops up again. After I keep clicking it for a while, it stops popping up, but I don't have the panel. What should I do?

---

### Post by dermotti on 2006-04-07
It only happen under that account?

---

### Post by æþeling on 2006-04-07
Yes, only under my account.

Looks like I screwed something up :(

---

### Post by frodon on 2006-04-07
To solve the problem, you need to get the panel working again (i know it could be the problem) and then save your session.
When your panels are completly dead, are you able to restart them with ? : ```
killall gnome-panel
```
I can reproduce this error each time i kill gdesklet with a kill command and then restart the panels, i will wait the next release of gnome (2.14) and if i can still generate this error i will fill a bug report.

---

### Post by æþeling on 2006-04-07
Thand frodon, that worked. Back in gnome now.

---

