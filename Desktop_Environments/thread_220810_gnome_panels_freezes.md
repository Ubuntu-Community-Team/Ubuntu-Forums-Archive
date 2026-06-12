---
title: "gnome panels freezes"
date: 2006-07-22
forum: Desktop Environments
---

### Post by rsFlud on 2006-07-22
Hi!
It happens always when i want to shutdown my comp. I simply close all my apps (e.g. Firefox, packet manager) and than click on "all-in-1 power button" to shutdown Ubuntu. After that my both, top and bottom, panels freezes. Window with reboot, shutdown, hibernate... doesn't show.
I'm only able to move my mouse, start programs (via lounchers on the desktop), open folders (on the desktop) etc.
Duration of this freeze is 2-4 minutes. Than window with power managment shows. I've noticed, when i click on the app icon at my frozen-panel nothing happens but after "thaw" it starts running.

My system spec.:
Ubuntu Dapper Drake 6.06 (64-bit)
Athlon 64 (3000+)
1 GB RAM
ATI Radeon X600

I'm despaired :evil: , ready for Gentoo or Slack.

---

### Post by rsFlud on 2006-08-05
Yeah!
I've found where's the problem. If iptalbes chain named INPUT has policy DROP problem occures but if policy is ACCEPT everything works fine. This is half measure.
Now... what the heck is with iptables:?:

//edit
OK. I've finally solved the problem. iptables may have default policy turned on DROP but should also have ACCEPT from localhost.
```
user@localhost: $ sudo iptables -A INPUT -s localhost -j ACCEPT
```

---

