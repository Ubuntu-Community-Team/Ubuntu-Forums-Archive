---
title: "Open application in chosen workspace at startup"
date: 2012-06-10
forum: Desktop Environments
---

### Post by zilog6502 on 2012-06-10
Hi guys,

I downloaded wmctrl yesterday in an attempt to open Midnight Commander automatically at startup in Workspace 3 of my XFCE desktop.

I cannot find any useful tutorials for wmctrl and the manpages are great at giving you a selection of options to use but nothing for correct syntax to set up a command or script.

Can anybody give me guidance on how to initiate MC in full screen on startup in a different workspace?

Many thanks in advance.

---

### Post by Toz on 2012-06-10
I would use devilspie instead ([https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie")) and a config file like:
```
if
    (is (window_name) "mc")
    (begin
       (set_workspace 2)
    )
)
```
...assuming that you are starting mc like this:
```
xfce4-terminal --title "mc" -x mc
```

---

### Post by brainwash on 2012-06-11
Here are the appropriate wmctrl commands (if you want to use wmctrl instead of devilspie):
```
#!/bin/sh
window="mc"
xfce4-terminal --title "$window" -x mc
wmctrl -r "$window" -t 2
wmctrl -r "$window" -b toggle,fullscreen
```

---

### Post by zilog6502 on 2012-06-26
Thanks guys.... sorry my response is late but haven't been on for a while.

I have used both solutions successfully with different applications now. Many thanks.

---

