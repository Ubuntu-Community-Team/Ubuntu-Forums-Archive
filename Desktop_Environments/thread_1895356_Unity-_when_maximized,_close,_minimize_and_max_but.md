---
title: "Unity- when maximized, close, minimize and max buttons are invisible"
date: 2011-12-14
forum: Desktop Environments
---

### Post by jRdbRR on 2011-12-14
the title says it all.  Its not that they disappear, as they are still clickable, and in the same order.  They are merely invisible it seems.  It started a couple of weeks ago, I didnt make any system changes, except maybe updates, so idk how the heck this happened!?

screenshotgiven

---

### Post by pastalavista on 2011-12-14
Do the buttons appear when the windows aren't maximized? Try, in terminal```
unity --reset
```

---

### Post by jimmydean886-2 on 2011-12-14
At first glance, I would say you are using Adwaita as your theme. This doesn't work so hot with Unity, because the fallback buttons are black.

Try using Radience if you want a lighter theme.

---

### Post by jRdbRR on 2011-12-15
ahh Thank You, unity --reset worked.

---

