---
title: "xfce4-notifyd --- have one notification positioned differently?"
date: 2014-04-03
forum: Desktop Environments
---

### Post by vasa1 on 2014-04-03
Xubuntu and Lubuntu use **xfce4-notifyd** and with **xfce4-notifyd-config** one can specify in which corner of the screen notifications will appear: 
[LIST]
[*]top left
[*]bottom left
[*]top right
[*]bottom right
[/LIST]
I've chosen notifications to appear at the bottom right.

But can I have just one notification (home-brewed) appear at the top left while the system notifications continue to appear in the bottom right as set with xfce4-notifyd-config?  

So, can I modify this script (as an example):

```
#!/usr/bin/env bash
      notify-send "$(date)"
```

to have the notification appear at the top left and not at the bottom right?

---

### Post by Toz on 2014-04-03
Hi vasa1.

Try this for your custom notification. It will change the location setting, send the notification, and reset the location. There is a small chance that another notification, if sent while the notification location is briefly changed, will appear at top left.
```

#!/usr/bin/env bash

# set notification location to top left
xfconf-query -c xfce4-notifyd -p /notify-location -s 0

# send notification
notify-send "$(date)"

# reset notification location to bottom right
xfconf-query -c xfce4-notifyd -p /notify-location -s 0
```

---

### Post by vasa1 on 2014-04-03
> **Toz said:**
> Hi vasa1.

Try this for your custom notification. It will change the location setting, send the notification, and reset the location. There is a small chance that another notification, if sent while the notification location is briefly changed, will appear at top left.
```

#!/usr/bin/env bash

# set notification location to top left
**xfconf-query -c xfce4-notifyd -p /notify-location -s 0**
# send notification
notify-send "$(date)"

# reset notification location to bottom right
**xfconf-query -c xfce4-notifyd -p /notify-location -s 0**
```

Toz, thanks for the code. I'll try it tomorrow morning. But the two lines in bold are identical?

---

### Post by Toz on 2014-04-03
Oops. Try this version:
```
#!/usr/bin/env bash

# set notification location to top left
xfconf-query -c xfce4-notifyd -p /notify-location -s 0
# send notification
notify-send "$(date)"

# reset notification location to bottom right
xfconf-query -c xfce4-notifyd -p /notify-location -s 3
```

Top Left = 0
Bottom Left = 1
Top Right = 2
Bottom Right = 3

---

### Post by vasa1 on 2014-04-03
> **Toz said:**
> Hi vasa1.

Try this for your custom notification. It will change the location setting, send the notification, and reset the location. ...
Works perfectly. Thanks!

---

