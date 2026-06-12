---
title: "force X11 to display in 1024 by 768"
date: 2006-02-23
forum: Desktop Environments
---

### Post by kasemodz on 2006-02-23
Alright, I have a headless server running. It used to be in another room connected to  a monitor but I decided to make it headless ( meaning no monitor) since i use my server througgh ssl and vnc. When it was connected to the monitor, it had the 1024 by 768 option in the system-preferences-screen resolution. However, now that the only thing connected is the power source and lan cable, it only displays 640 by 480. How do I force X to display in 1024 by 768. I'm running gnome right now. Here is my X configuration. (/etc/X11/xorg.conf)

---

### Post by shams2 on 2006-02-23
did you try the System -> preferences -> Screen Resolution.

---

### Post by kasemodz on 2006-02-23
[QUOTE=shams2]did you try the System -> preferences -> Screen Resolution.[/QUOTE]
"When it was connected to the monitor, it had the 1024 by 768 option in the system-preferences-screen resolution." as stated above.

---

### Post by shams2 on 2006-02-23
your xorg.conf looks ok, click on the Screen Resolution arrow and change to the 1024.

---

### Post by janunezc on 2008-05-10
> **shams2 said:**
> your xorg.conf looks ok, click on the Screen Resolution arrow and change to the 1024.

shams2, I am sorry for saying this but you are not reading!

When there is no monitor, the ONLY resolution option is 640 x 480!

How to configure the system to work with no monitor @ 1024 x 768??

---

