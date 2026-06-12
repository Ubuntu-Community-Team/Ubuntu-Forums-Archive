---
title: "VNC server and Applications &amp; System menu problems"
date: 2006-02-20
forum: Desktop Environments
---

### Post by shufla on 2006-02-20
Hello,

I have installed Ubuntu Breezy on system without monitor/keyboard/mouse. I've set up vncserver in xinetd.d with:
```

/usr/bin/Xvnc -inetd -broadcast -geometry 1024x768 -query amiga -depth 24 -once -fp unix/:7100
```

I've got strange problem with Gnome Applications and System menus - they are disappear after less then 1 second. Installing menu package and running update-menus as root do not help.

Debian sid/sarge with same VNC configuration runs without any problems. Where could I find more info? How should I debug that situation?

Best Regards,
Luke

PS. Same problem while accessing remotly by X (eg. Xnest)

---

