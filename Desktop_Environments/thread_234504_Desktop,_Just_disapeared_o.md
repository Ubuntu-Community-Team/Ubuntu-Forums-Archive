---
title: "Desktop, Just disapeared :o"
date: 2006-08-11
forum: Desktop Environments
---

### Post by orasis on 2006-08-11
I am using Xubuntu, and after installing filerunner and Gftp - I rebooted my pc (not because I installed software, another reason)

So anyways, when I re-loaded the system -... my task bars are gone :o

anyone have an idea what just happened?

---

### Post by aysiu on 2006-08-12
Open a terminal.

Type *xf* (but do not press **Enter**)

Then press the **Tab** key twice.

I believe the command you're looking for is *xftaskbar* or *xfce4-taskbar*.

---

### Post by niceguy123 on 2007-11-12
Wow, Thanks. That worked. Could you tell me why it disappeared to begin with?

---

### Post by aysiu on 2007-11-12
No idea why they disappeared.

---

### Post by niceguy123 on 2007-11-12
I found that when I type xfce4-panel in the terminal the toolbars show, but then when I close the terminal they disappear again. 

Any ideas?

---

### Post by aysiu on 2007-11-12
> **niceguy123 said:**
> I found that when I type xfce4-panel in the terminal the toolbars show, but then when I close the terminal they disappear again. 

Any ideas?
Try ```
xfce4-panel &
```

---

### Post by niceguy123 on 2007-11-12
That worked, Thanks.

---

