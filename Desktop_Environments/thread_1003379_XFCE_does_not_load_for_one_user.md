---
title: "XFCE does not load for one user"
date: 2008-12-06
forum: Desktop Environments
---

### Post by thunderboltz on 2008-12-06
The XFCE desktop environment doesnt load for one user alone on the system. At the gdm login screen the user selects XFCE and when he logs in, the xfce splash screen (rat on the X) comes, and then a blank blue screen appears. No toolbars/task bars. Only ctrl+alt+del seems to work, and that locks the screen and starts the screensaver.

Any help on what is going on, and how to correct it would be most welcome.

Thanks in advance.

PS: I'm using debian lenny/testing

---

### Post by john.nicholls on 2008-12-07
For that one user, I would suggest removing the Xfce configuration files under /~/.config/xfce4 and letting them regenerate.

---

### Post by JeffoOfMetal on 2008-12-07
I had this with Xubuntu.

I'm not sure if whatever you're using will do this, but I right-clicked the desktop, hit *Desktop Settings*, and enabled it so I could right click the desktop to get the Applications menu.

Then, I started Terminal and typed:

```
xfce4-panel
```

From there, I went *Applications>Settings>Settings Manager.* I selected Autostarted Apps and added the command *xfce4-panel.*

Again, I'm not sure if this would work in your situation.

---

### Post by thunderboltz on 2008-12-12
Nopes. Tried both the solutions to no avail. Any other ideas, anyone? This is kind of very frustrating, as I really want to switch over to xfce...

---

