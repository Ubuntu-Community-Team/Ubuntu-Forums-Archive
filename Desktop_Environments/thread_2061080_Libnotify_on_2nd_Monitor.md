---
title: "Libnotify on 2nd Monitor"
date: 2012-09-21
forum: Desktop Environments
---

### Post by A4orce84 on 2012-09-21
Hello Everyone,

I have a desktop environment with 2 monitors, and I want the libnotifications (that work with pidign, rhythmbox, etc.) to display on the other monitor.

I tried changing the "default" monitor option in the Monitors settings, but that did not work.

Can anyone assist me please?

Thanks,


--Asif

---

### Post by josephmills on 2012-09-21
can you try this open your terminal and enter in 

[COLOR="Red"][SIZE="3"]WARNING DO MORE GOOGLEING 
[/SIZE][/COLOR]


```
gconftool-2 -s -t string /apps/notify-osd/multihead_mode focus-follow
```

that should send to the monitor that is in use. or the active one I would think

---

