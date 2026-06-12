---
title: "Delay lxpanel autostart in Lubuntu"
date: 2012-07-14
forum: Desktop Environments
---

### Post by ankspo71 on 2012-07-14
Sometimes lxpanel starts faster than the graphical environment can finish loading and this can cause problems with panel transparency (or compositing) and proper panel alignment. This might be more of a problem with logging out and logging back in instead of restarting the system, as it was in my case. I had to come up with my own solution since Lubuntu's desktop depends on the lxsession configuration file which doesn't support using the sleep command (as far as I know). 


**Step 1**

First backup Lubuntu's lxsession autostart configution file:
```

sudo cp /etc/xdg/lxsession/Lubuntu/autostart /etc/xdg/lxsession/Lubuntu/autostart.backup
```

Now open Lubuntu's lxsession autostart configution file for editing:
```
 gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart
```

and find the line that says
```
@lxpanel --profile Lubuntu
```

and replace it with these lines:

```
# lxpanel --profile Lubuntu
@lxpaneldelay
```


Save the document and exit Leafpad.


**Step 2**

Create a script called "lxpaneldelay"
```
sudo touch /usr/bin/lxpaneldelay
gksudo leafpad /usr/bin/lxpaneldelay
```

Now paste in the following code:
```

#!/bin/sh

sleep 4 && lxpanel --profile Lubuntu
```


Save the document and exit Leafpad. (sleep 4 means lxpanel will be delayed by 4 seconds)



**Step 3**

Make the script executable.
```
sudo chmod +x /usr/bin/lxpaneldelay
```





**Step 4 **
Logout and login to see if the changes make a difference.



**Removal instructions:**
```

sudo cp /etc/xdg/lxsession/Lubuntu/autostart.backup /etc/xdg/lxsession/Lubuntu/autostart
sudo rm /usr/bin/lxpaneldelay
```

(Be extra careful using rm commands, by the way)

---

### Post by Rexilion on 2012-07-14
You could also just try delaying for a while and do:

killall -SIGUSR2 lxpanel

or SIGHUP or SIGUSR1. This works for me with xfce's mailwatch daemon. This functionality is hardly documented.

As for the 'sleep' function that is 'not supported'. You can use sudo for that.

---

