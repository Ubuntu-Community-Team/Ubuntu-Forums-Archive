---
title: "LXDM does not work on startup"
date: 2016-05-29
forum: Desktop Environments
---

### Post by Voc on 2016-05-29
Hey guys,

I decided to switch over from the default Lubuntu login manger LightDM to LXDM.  However, every time I start up the computer I am presented with a command-line login and have to press Ctl+Win+F7 to get to the LXDM.  I tried running the following in terminal:
```

sudo systemctl enable lxdm
sudo lxdm systemd
sudl lxdm -reconfigure

```
but none of them seemed to help.  I'm wondering what else I might try to do so LXDM starts automatically.  I'm using Lubuntu 16.04 if it helps.

Thanks for the help,
Luke

---

