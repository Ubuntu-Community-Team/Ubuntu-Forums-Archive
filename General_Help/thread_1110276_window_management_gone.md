---
title: "window management gone"
date: 2009-03-29
forum: General Help
---

### Post by Loetje on 2009-03-29
Hi,

Since a couple of days (probably caused by a hard power-off) i have no more window management.

That is, everything works, but the programs no longer have windows around them that i can minimize or close. Also i can't alt-tab to another program. When i'm inside a program (say firefox) the only way to show my desktop again is to exit.

Any ideas how to fix this?

---

### Post by ryanhaigh on 2009-03-29
If you are using compiz then the window-decorations plugin has probably been turned off somehow. Switch back to metacity temporarily, change the setting in the compiz config manager (advanced desktop effects in preferences) and then switch back to compiz.

To do this open a terminal (or if alt-f2 is working use that) and run the command ```
metacity --replace
```. Make the required changes in the compiz configuration app and then restart compiz using ```
compiz --replace
```

---

