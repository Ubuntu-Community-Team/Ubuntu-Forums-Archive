---
title: "Kubuntu/Beryl Shutdown and Restart Issue - Buttons are Missing"
date: 2007-04-08
forum: Desktop Effects &amp; Customization
---

### Post by lazyrussian on 2007-04-08
Hi,

I'm a Kubuntu Edgy User / Beryl User. I'm having one problem, the shutdown/restart buttons are missing when I push Log Out. Only the, "End Current Session" Pops up.

I've been logging out manually through the konsole/terminal.

Is there a way I can fix this?


Here's my startxgl file

```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec startkde

```

---

### Post by danhm on 2007-04-08
Try changing it to this:

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec startkde
```

---

### Post by lazyrussian on 2007-04-08
Danhm,

Thanks for the effort, but it didn't work :(

---

