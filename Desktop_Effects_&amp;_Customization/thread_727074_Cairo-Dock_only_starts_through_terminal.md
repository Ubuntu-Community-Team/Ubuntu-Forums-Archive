---
title: "Cairo-Dock only starts through terminal"
date: 2008-03-17
forum: Desktop Effects &amp; Customization
---

### Post by Tews on 2008-03-17
I installed Cairo-dock but the only way I can launch it is through the Terminal, and when I close the terminal, it closes Cairo Dock as well .... What am I doing wrong :confused:

---

### Post by Lord Illidan on 2008-03-17
In order to prevent it closing, try doing

```
cairo-dock & disown & exit
```

---

### Post by Tews on 2008-03-17
That di it!!

However ... The background theme is only 2D ... how do I enable the 3D effect?

---

