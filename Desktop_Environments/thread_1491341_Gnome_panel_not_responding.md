---
title: "Gnome panel not responding"
date: 2010-05-23
forum: Desktop Environments
---

### Post by philkahly8 on 2010-05-23
I have Ubuntu with a Gnome GUI. When I tried to add a third panel to the left side, it didn't respond for a moment then two panels appeared on that side and all the panels froze. Whenever I log out, shut down or restart, it tells me that Panel is not responding and does not give me the option of closing it. The whole left side of the top and bottom panels are blank now. I can't use the menus or my quick launch icons. When I right click on any of the panels nothing comes up. My other user account and my root profile work fine, (but use different themes), and I can use my account with KDE or XFCE. Anyone know how to fix this?

---

### Post by wojox on 2010-05-24
Try and reset the panels:

```
gconftool --recursive-unset /apps/panel
```

```
pkill gnome-panel
```

---

### Post by philkahly8 on 2010-05-24
I fixed it before I saw your message by logging into failsafe mode and deleting the new panels. Then when I logged back into regular Gnome it was fine. Thanks anyway, if the problem comes back I'll try your method. Thanks again.:P

---

