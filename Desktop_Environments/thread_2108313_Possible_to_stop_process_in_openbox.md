---
title: "Possible to stop process in openbox?"
date: 2013-01-24
forum: Desktop Environments
---

### Post by drfox on 2013-01-24
There is probably pretty esoteric, but...
I have installed ubuntu server in virtual box.
I installed xfce-desktop, which I run on my desktops...everything worked fine.
I wanted a lighter install, so I removed xfce and intalled openbox so that I can have a GUI.
I have an autostart program which is hanging.
How do I break that hanging program and continue the booting process? I've tried Control-C, Control-Q, :exit and :quit

Thanks for any suggestions.

---

### Post by raja.genupula on 2013-01-24
this is the place where auto-start programs will configure. check what you got there

```
cd ~/.config/autostart/
```

---

