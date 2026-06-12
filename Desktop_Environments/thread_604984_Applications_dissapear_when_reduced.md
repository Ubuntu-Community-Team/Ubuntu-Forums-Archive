---
title: "Applications dissapear when reduced"
date: 2007-11-06
forum: Desktop Environments
---

### Post by Pinpoint Focus on 2007-11-06
I have reduced visual effects to None, and when I open Applications, use them, then minimize them they dissappear, as though I have closed them.

---

### Post by ohzopants on 2007-11-07
Are they still running? Try using
```
ps --user=yourusername
```

to see if they are in fact still running.

If they are still running I suspect you may have accidentally removed the "window list" applet from your panel.

---

