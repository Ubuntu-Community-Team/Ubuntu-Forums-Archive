---
title: "shutdown launcher"
date: 2014-12-25
forum: Desktop Environments
---

### Post by trav9595 on 2014-12-25
This is the code for a shutdown launcher when I view it in gedit
 ...why does it not work??

[Desktop Entry]
Version=1.0
Type=Application
Name=OFF
Comment=
Exec=shutdown -p now
Icon=xfsm-shutdown
Path=
Terminal=false
StartupNotify=false

---

### Post by schragge on 2014-12-25
You need to be root/sudo to be able to execute *shutdown*. Besides, it's the captial P:
```
shutdown -[color=red]P[/color] now
```

---

### Post by trav9595 on 2014-12-25
I got it to work with Ph instead of p
big improvement over the stock shutdown

---

