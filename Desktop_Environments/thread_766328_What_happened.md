---
title: "What happened??"
date: 2008-04-25
forum: Desktop Environments
---

### Post by The Last Soul on 2008-04-25
What happened to my desktop? The bar at the top and bottom is gone. How do i get it back?? (I have tried to restart the computer)

Now is look likes this:
 [ATTACH]67094[/ATTACH]


Can anyone help me??

---

### Post by angry_johnnie on 2008-04-25
Well, you just need to launch gnome-panel.

The easiest way would be to try Alt + F2 and then type **gnome-panel**

If that doesn't do it (I think gnome-panel has to be there in order for Alt + F2 to work), you could open that folder you have on the desktop.


In that folder, navigate to the **/usr/bin/** directory.

Once you're there, look for **gnome-terminal**.

When you find it, double click on it to launch it.

Then, in your terminal, type **gnome-panel & disown**.

If it tells you that gnome-panel is already running, you could try:

```
killall gnome-panel
```

It should come back immediately.

---

### Post by The Last Soul on 2008-04-25
It worked. Thank you.

It showed up that the panel wasn't installed :confused:
After I installed it, I ran the **gnome-panel & disown** it worked again.

Thanks

---

