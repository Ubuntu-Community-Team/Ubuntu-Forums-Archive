---
title: "Panels not visible"
date: 2007-06-01
forum: Desktop Environments
---

### Post by jayman76 on 2007-06-01
Installed beryl and have it running. Not sure if it's exactly a beryl problem though. After login the splash screen displays, the background image loads, but none of the panels load......

---

### Post by bmartin on 2007-06-01
Are you using XGL? If so, it probably has to do with the commands in your startxgl.sh file (or whatever you named it). Make sure that it's loading the gnome-session program in there. Refer back to the setup instruction for more details.

gnome-session is a complicated script that loads up many of the other things that you're used to.

---

### Post by pbw on 2007-06-01
If you're in gnome run ```

killall -9 gnome-panel && gnome-panel &

```
kde
```
killall -9 kicker && kicker &

```
Or xfce
```

killall -9 xfce4-panel && xfce4-panel &
```

-- pbw

---

