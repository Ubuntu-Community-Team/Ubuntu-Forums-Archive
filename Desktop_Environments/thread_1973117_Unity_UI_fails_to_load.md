---
title: "Unity UI fails to load"
date: 2012-05-04
forum: Desktop Environments
---

### Post by Tornikee on 2012-05-04
Hello, after running the 12.04 since its release, this is the first major issue I've come across. Last night the Unity UI (launcher, dash, panel) failed to load after I had tried the Unity 2D (which runs w/o any issue) and GNOME sessions and logged back in to 'Ubuntu' session. The autorun applications do run, but the UI is completely invisible and inaccessible.

Is this a known bug?

---

### Post by StApnea on 2012-05-04
Have you tried?
```
unity --reset
```

---

### Post by Tornikee on 2012-05-04
Um, is there a shortcut for starting terminal? So that I can enter that afterwards.

---

### Post by StApnea on 2012-05-05
Try ```
Control-Alt-T
```

If that doesn't bring up a terminal window press```
Control-Alt-F2
```

That will bring you to what looks like a full screen terminal. You'll have to login and then type in ```
unity --reset
```

To get back to the GUI press ```
Control-Alt-F7
```

---

### Post by Tornikee on 2012-05-06
Thanks a lot, that worked just fine.

---

