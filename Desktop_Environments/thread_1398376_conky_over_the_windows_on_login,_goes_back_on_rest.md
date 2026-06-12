---
title: "conky over the windows on login, goes back on restart of conky."
date: 2010-02-04
forum: Desktop Environments
---

### Post by hariks0 on 2010-02-04
Hi all, hope the title says it all. When I login, conky is started automatically [which I want to] and stays on top of the windows opened later. If I kill conky and start it again using Alt+F2 or Gnome-do, it goes back to the desktop becomes transparent and disturbing no windows. Also then I can right click on conky to access the desktop context menu, which is not possible with the initial conky.

---

### Post by mobilediesel on 2010-02-04
> **hariks0 said:**
> Hi all, hope the title says it all. When I login, conky is started automatically [which I want to] and stays on top of the windows opened later. If I kill conky and start it again using Alt+F2 or Gnome-do, it goes back to the desktop becomes transparent and disturbing no windows. Also then I can right click on conky to access the desktop context menu, which is not possible with the initial conky.

Try here: [http://conky.linux-hardcore.com/?page_id=503](http://conky.linux-hardcore.com/?page_id=503)
basically you set up a small startup script for Conky that has a sleep command to make sure the window manager is running fully before Conky runs.
```
#!/bin/sh
# click to start, click to stop
 
if pidof conky | grep [0-9] > /dev/null
then
exec killall conky
else
sleep 10  # sleep not required for xfce on startup - 30 or more for others
conky -c ~/Conky/conkymain &
#sleep 3
conky -c ~/Conky/conkytext &
exit
fi
```

---

