---
title: "How to reverse mac4lin"
date: 2009-08-28
forum: Desktop Environments
---

### Post by Bearded-flower on 2009-08-28
I was messin around with mac4lin, and i swapped the buttons around, how do i reverse this so it goes back to normal???

---

### Post by urosg3 on 2009-08-28
[http://www.ubuntu-rs.org/forum/files.php?pid=76067&aid=1074]("http://www.ubuntu-rs.org/forum/files.php?pid=76067&aid=1074")

Try this, uninstall  script for  Mac4Lin.

---

### Post by prshah on 2009-08-28
> **Bearded-flower said:**
> I was messin around with mac4lin, and i swapped the buttons around, how do i reverse this so it goes back to normal???

Open gconf-editor by pressing Alt+F2, and giving the command ```
gconf-editor
```; then browse to /apps/metacity/general/button_layout
, and change the layout order. The button preceding the ":" will appear in the left corner of the title, and the buttons succeeding the ":" will appear in the right edge.

As an example, I use```
menu:minimize,maximize,spacer,close
```

---

