---
title: "Network manager in Lxde"
date: 2010-07-23
forum: Desktop Environments
---

### Post by babai on 2010-07-23
I just installed lxde on an ubuntu lucid box and after logging into it I found that the network manager applet doesnt start automatically and hence no internet connection. Though I could easily setup the net using ifconfig, I want to use network manager as this pc is used by my brother whos a beginner. In the terminal if I give "nm-applet &" the applet starts and the notification daemon states "connection established" but still internet is not available. So how can I configure the network manager in lxde?

---

### Post by clrg on 2010-07-23
Network manager also has a service, the applet is just the front-end. Do a "sudo service network-manager start" instead (if nm-applet doesn't start automatically, start it afterwards). If you want it started every time the users logs in, make a script with the commands you would use too, for example

```

#!/bin/bash
sudo service network-manager start
nohup nm-applet &
exit 0

```

Give it to root, make it executable, and move it somewhere in your $PATH

```
sudo chown root:root myscript; chmod 755 myscript; mv myscript /usr/local/bin/myscript
```

Then add an autostart application to LXDE containing your script (don't know if there is such an option, in Gnome its possible to do that using the GUI) and relogin in order to test it.

---

