---
title: "Skype icon is misplaced in XFCE panel"
date: 2012-07-29
forum: Desktop Environments
---

### Post by ruza on 2012-07-29
I just read an old thread, not answered. 

I discovered strange behavior of the XFCE panel. When loading Skype (autostart at login) the icon is partially hidden under other panel items or lost at all. Restarting Skype helps, as well as resizing the xfce4-panel (and putting it back to original size)

I know that this is not an important problem, it is purely aesthetic problem, but still, it is a problem. 

I guess that i could solve it with changing the skype tray icon, but, i can not seem to find it anywhere....

---

### Post by Toz on 2012-07-29
Can you post an screenshot of it?

Maybe if you delayed the startup of skype to give the panel time to initialize would help? Create a script with the following contents:
```

#!/bin/bash
sleep 5
skype

```
... make the script executable and put the script in Settings Manager -> Application autostart.

---

### Post by ruza on 2012-07-29
as soon as it happens i will put screenshot of it... it does not happen everytime... i dont need skype as soon as i login, but that does not happen exclusively at startup time - it happens more often at that time. Problem is that i cannot determine what causes the error...

---

