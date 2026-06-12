---
title: "Window decorations less robust in Natty"
date: 2011-05-13
forum: Desktop Environments
---

### Post by peterdm on 2011-05-13
Since the upgrade to Natty, the Window Decorations easily break on my system. When running/debugging a Java app from Eclipse IDE, often the window decorations are gone after the Java app pops up a dialog. Both "Unity" and "classic" show the symptom.

```
Architecture: 32-bit Ubuntu (on 64-bit capable hardware)
Java version: JDK 1.6 update 24
Debugging option for running the app: -Dsun.awt.disablegrab=true
```

Anyone else having stability problems with the Window Decorations (Compiz)?

Peter

---

### Post by daniq on 2011-05-26
I have the same problem, solving it by:
```
compiz --replace
```

---

