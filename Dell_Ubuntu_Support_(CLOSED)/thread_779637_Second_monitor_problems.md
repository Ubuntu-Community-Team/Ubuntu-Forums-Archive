---
title: "Second monitor problems"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeff.kroge on 2008-05-02
I am having a problem with my new Dell Inspiron 530 Running Ubuntu and a nvidia (gforce 8 series) graphics card. I tried tonight to plug in a second monitor and it isn't providing a signal to the 2 different monitors I tried in the second port on the graphic card. When I look at the screen and graphics preferences dialog in Ubuntu it only shows one monitor. the driver that is selected is nvidia.

---

### Post by damis648 on 2008-05-02
press fn+f8 or whatever key is is that shows two little monitors on it... if that doesnt work, press alt+f2 and type
```
nvidia-settings
```
and configure it in the second tab, "X Server display configuration"

---

