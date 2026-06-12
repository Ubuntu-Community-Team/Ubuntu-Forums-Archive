---
title: "Fonts not appearing."
date: 2007-03-17
forum: Desktop Environments
---

### Post by jimw on 2007-03-17
I'm running Edgy, and I can't seem to make cuneiform fonts appear as anything but standard latin letters.  The main font I'm working with is called NeoAssyrianRAI.

I don't have any difficulty with any other fonts. (&#1099;&#1091;&#1091; &#1094;&#1088;&#1092;&#1077; &#1064; &#1100;&#1091;&#1092;&#1090;?)

Can anyone help me out?

Thanks

JimW

---

### Post by Najand on 2007-03-17
Open a terminal and try to run:
```

sudo fc-cache -fv

```
And then restart X using Ctrl+Alt+BackSpace
Try to reconfigure your Display  fonts again and see if it works or not.

---

