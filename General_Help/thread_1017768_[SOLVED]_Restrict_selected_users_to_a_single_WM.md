---
title: "[SOLVED] Restrict selected users to a single WM"
date: 2008-12-21
forum: General Help
---

### Post by blackgr on 2008-12-21
I would like to know how can i restrict couple of users to only use a Window manager of my choise and not by default, gnome. I thought of changing the permitions of the /usr/bin/gnome-session from -rwxr-xr-x to -rwxr-xr-- so than only users inside "root" group will be able to use gnome. Is there any better and "cleaner" way to do it? 

thnx

---

### Post by blackgr on 2008-12-21
Seems like i found a better way to do it. I created a script named "user1res" that checks users before starting a session.

```
#! /bin/bash

if [ "`whoami`" == "user1" ];
then
/usr/bin/openbox-session
else
/usr/bin/gnome-session
fi

```

then moved it to /usr/bin and after that i edited /usr/share/xsessions/gnome.conf so that it will run my script insteed of gnome-session

---

