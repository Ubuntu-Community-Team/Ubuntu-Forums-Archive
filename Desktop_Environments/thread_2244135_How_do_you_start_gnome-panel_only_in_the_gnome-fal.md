---
title: "How do you start gnome-panel only in the gnome-fallback session?"
date: 2014-09-13
forum: Desktop Environments
---

### Post by CantankRus on 2014-09-13
For some reason gnome-panel stopped starting with my gnome-fallback session.
I use unity mainly so i can't just add it to Startup Applications.
So I would like to know how to autostart only in the gnome-fallback session.

PS: Shows as **Gnome Flashback** at the greeter
but terminal shows...
```
@Trusty:~$ echo $DESKTOP_SESSION
**gnome-fallback**

@Trusty:~$ ls /usr/share/xsessions
cairo-dock.desktop  gnome-fallback-compiz.desktop  ubuntu.desktop
gnome.desktop       gnome-fallback.desktop         xfce.desktop
```

---

### Post by CantankRus on 2014-09-14
Bumpa-lumpa

---

### Post by CantankRus on 2014-09-15
Can't find a solution so just wrote a script and placed in Startup Applications.
Checks $DESKTOP_SESSION and starts gnome-panel and plank if in a fallback session.
```
#!/bin/bash
#set -x

if [[ $DESKTOP_SESSION == "gnome-fallback" || $DESKTOP_SESSION == "gnome-fallback-compiz" ]]
	then echo "gnome-fallback session"
		gnome-panel &
		plank
	else echo "Not gnome-fallback session"
fi
exit 0
```

---

