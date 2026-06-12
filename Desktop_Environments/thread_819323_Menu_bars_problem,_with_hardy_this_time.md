---
title: "Menu bars problem, with hardy this time"
date: 2008-06-05
forum: Desktop Environments
---

### Post by sipickles on 2008-06-05
hi,

We have a crappy old laptop here at work, and it actually runs Xubuntu well (Amazing work by the team at Xubuntu!)

However today, the menu and tool bars have vanished.

The desktop and icons are still there and the mouse is working.

Google found some others who have had this problem but that was with older version of Ubuntu (edgy/feisty). I couldn't find a fellow sufferer with Hardy.

As suggested in those posts, typing xfce-panel in a terminal restored the bars, but they disappear when the terminal is closed or the system is rebooted.

Can anyone help fix this?

Thanks

Simon

---

### Post by mali2297 on 2008-06-05
Use the run dialog (Alt+F2) to execute
```

xfce4-panel

```
When you logout, choose to save the session. If you don't see that option, check the *Sessions and Startup* settings.

---

