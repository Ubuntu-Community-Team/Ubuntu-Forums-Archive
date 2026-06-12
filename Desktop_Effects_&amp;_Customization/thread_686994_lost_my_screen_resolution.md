---
title: "lost my screen resolution"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by gallaharsha on 2008-02-03
i have intel d101ggc motherboard with integrated ati xpress200 chipset .
im new to linux and have installed ubuntu 7.10 yesterday.
everything was working until i enabled the ati drivers from "restriceted drivers manager"
i dont know some how the screen resolution gone to 800*600 . i had 1024*760 resolution on windows.
kindly help me with a solution.
also tell me how i could use the ati chipset with ubuntu...
THANKS IN ADVANCE.

---

### Post by Rupertronco on 2008-02-03
Could you please post a copy of your xorg.conf file?

The way to do that is to open a terminal and type 

```
gedit /etc/x11/xorg.conf
```


Then copy and paste the file that it opens.

---

### Post by overdrank on 2008-02-03
> **Rupertronco said:**
> Could you please post a copy of your xorg.conf file?

The way to do that is to open a terminal and type 

```
gedit /etc/x11/xorg.conf
```


Then copy and paste the file that it opens.

HI and I believe the command is ```
cat /etc/X11/xorg.conf
``` 
and to edit the file use ```
gksudo gedit /etc/X11/xorg.conf
``` The X is capital

---

