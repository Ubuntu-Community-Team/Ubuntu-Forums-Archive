---
title: "Crontab Log"
date: 2016-08-01
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-08-01
Folks,

I manage a girlfriend's Ubuntu 14.04 remotely using ssh and on occasions VNC. For some reason every so often her computer loses wifi connection and I have to call and get her to reconnect. This it does fine.

To try and keep connection alive I decided to enter sudo crontab -e and enter the following;

```
15 6 * * * nmcli c up id linksys
```

Now this works fine manually but if I enter ```
sudo cat syslog | grep nmcli
``` it finds nothing.

The same code but with cron finds the daily cron tasks, what am I doing wrong with this?

Geffers

---

