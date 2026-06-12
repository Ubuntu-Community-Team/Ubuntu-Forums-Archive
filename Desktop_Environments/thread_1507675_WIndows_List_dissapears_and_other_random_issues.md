---
title: "WIndows List dissapears and other random issues"
date: 2010-06-11
forum: Desktop Environments
---

### Post by slipknott on 2010-06-11
Hello,
 

 I am running 10.04 64-bit and randomly, once every week or so, the Show Desktop, Windows List, Workspace Switcher and Trash icons all disappear from my bottom panel. I can still use Alt+Tab to switch between the items but i have to go back into Add to panel... and manually add all of these options to the panel again. I can't figure out why this is happening and my knowledge of linux is still low so i'm having some difficulty solving the issue. I am also using the Darker Theme theme like i do on other pcs, but only experience it on this one. Thanks for any help you can provide!
 

 Slip


**Edited to only include one issue instead of the two in the original post**

---

### Post by gingivere0 on 2010-06-11
For the first issue, I would try this command in the terminal:

```
killall gnome-panel
```

It may or may not work, hope for the best!

---

