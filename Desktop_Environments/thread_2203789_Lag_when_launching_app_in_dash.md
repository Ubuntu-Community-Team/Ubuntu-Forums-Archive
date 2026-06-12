---
title: "Lag when launching app in dash"
date: 2014-02-05
forum: Desktop Environments
---

### Post by jeremy9856 on 2014-02-05
When I launch an application in the Dash with the mouse there is a latency of about half a second whereas if I launch the application by typing its name and by press enter it is instantaneous. 
Is this a bug in Unity ? Is it the same for you ?

---

### Post by jeremy9856 on 2014-02-05
OK I found how to fix it

```
$ dconf write /com/canonical/unity/double-click-activate false
```

---

