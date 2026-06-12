---
title: "How to restore gnome-ppp to panel?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by rogblake on 2006-09-20
Gnome-ppp was configured so that when it connected, an icon would be placed in the panel notification area where one could click on it to disconnect. I stupidly managed to select "remove from panel" instead, and now there is no icon for the connection. To disconnect I need to "kill -9" gnome-ppp and pppd from a shell prompt. I've tried disabling and re-enabling gnome-ppp's "Dock in notification area" option, but this has not helped. How can get this feature working again?

---

### Post by andypaxo on 2006-09-20
Do you mean that you removed the notification area from the panel, not just the gnome-ppp icon?
In this case, just right click on the panel, Select 'Add to panel' and choose 'Notification Area'.
You can reposition the notification area by dragging it around with the middle mouse button

---

### Post by rogblake on 2006-09-20
I thought it was just the gnome-ppp icon, but I'll double-check when I get back to that computer. I see now there is a "Modem Monitor" applet available through the "Add to panel" function, will give that a try.

---

### Post by rogblake on 2006-09-21
You were right, it was the notification area that was removed. When I went to disconnect I must have missed the gnome-ppp connection icon and right-clicked on the notification area itself. I added the notification area back to the panel and it's back to normal. Thanks!

---

