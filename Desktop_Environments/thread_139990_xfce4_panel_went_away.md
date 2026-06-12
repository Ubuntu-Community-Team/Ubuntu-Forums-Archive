---
title: "xfce4 panel went away"
date: 2006-03-05
forum: Desktop Environments
---

### Post by alex2035 on 2006-03-05
Installed XFCE4 from universe repositories, went like silk but after a while the panel went away, xinitrc says "panel crashed, etc etc":confused: 
any hint on how to get it back? thanx
alex

---

### Post by astoltz on 2006-03-05
I think it's just ```
xfce-panel &
``` on the command line.  It's been a while since I've run XFCE though.

---

### Post by taurus on 2006-03-05
[QUOTE=astoltz]I think it's just ```
xfce-panel &
``` on the command line.  It's been a while since I've run XFCE though.[/QUOTE]
It's 
```

xfce4-panel &

```

---

### Post by alex2035 on 2006-03-05
OK that was nice, thank you, but...I got the panel as long as I keep xterm open (where I issued the command). having this open for the rest of the session is not very comfortable. could I just recover the panel  to stay there as it should be?

---

### Post by aysiu on 2006-03-05
Press Alt-F2 and then type ```
xfce-panel &
``` Make sure you save your session.

---

### Post by astoltz on 2006-03-05
The ampersand at the end of the command means "run this command in the background".  You should get a command prompt back after you do the "xfce4-panel &" command.  You might have to hit the enter key twice but when you get the command prompt back, you should be able to close the terminal without closing the panel.  Oh yeah, the Atl-F2 thing will work also - don't think you need the ampersand in that case. And just to clarify, it is xfce**4**-panel.

---

### Post by alex2035 on 2006-03-08
thank you, i just saved the session and it works.

---

