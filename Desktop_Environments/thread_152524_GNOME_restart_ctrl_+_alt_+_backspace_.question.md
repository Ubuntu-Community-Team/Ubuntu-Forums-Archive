---
title: "GNOME restart ctrl + alt + backspace .question"
date: 2006-03-30
forum: Desktop Environments
---

### Post by Felix21685 on 2006-03-30
after some hardware issues i finally figured out how to have win xp on my sata and ubuntu 5.1 on my 40GB IDE.


when i restart GNOME or X i guess you guys call it
i get to a fullscreen prompt..
i can get back in with```
sudo /etc/init.gdm restart
```

but i thought it was supposed to restart normal by itself.

how can i set ubuntu to restart like the command above without having to type it in each time?

thx in advance,
-Felix

---

### Post by hw-tph on 2006-03-30
Ctrl+Alt+Backspace is sort of an emergency exit. Does your environment freeze so often that using this is the only way out? If not you should exit gnome gracefully using System -> Logout, or just restart the gdm script from a terminal.


Håkan

---

### Post by Felix21685 on 2006-03-30
aha ok..
i thought it was a fast easy way of restarting GNOME and just logging back in and tada..

thanks for clearing that up

---

