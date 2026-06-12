---
title: "wmctrl after upgrade to Maverick"
date: 2010-10-24
forum: Desktop Environments
---

### Post by lulaz on 2010-10-24
Hello,

On Lucid Lynx I used to have a shortcut command for switching from one desktop to another via SSH (while logged as root).
```

DISPLAY=":0.0" wmctrl -s 0
DISPLAY=":0.0" wmctrl -s 1

```After upgrade to Maverick this no longer works. I get:
```

# DISPLAY=":0.0" wmctrl -s 1
No protocol specified
Cannot open display.

```If I run this command as user (which is logged in gnome - dont know is it important) command returns nothing, but it doesnt switch the desktops.

Please help ;(

---

