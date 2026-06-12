---
title: "How to undo and disable a previously set timed shutdown?"
date: 2009-03-21
forum: General Help
---

### Post by Pipps on 2009-03-21
I often set a timed shutdown using the following command:

```
sudo shutdown -h +60
```
ie: for a 60-minute timed shutdown.

However, sometimes I change my mind, and would like to undo this shutdown.

How can I do this, and stop the system from adhering to the previously set timed shutdown operation? Thank you.

---

### Post by jbrown96 on 2009-03-21
Check out the manual pages. ```
man Command
``` For shutdown, it looks like you can run ```
sudo shutdown -c
```

---

