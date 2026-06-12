---
title: "Screenlets drawn behind the desktop (not visible)"
date: 2009-06-09
forum: General Help
---

### Post by ricardofilipemoreira on 2009-06-09
hi! i have ubuntu 9.04 with screenlets installed and a clock screenlet to run on startup. i don't know why but it starts up behind the desktop. i have set to on the options "always on top", "sticky" and "locked". "treat as widget" is off, and the widget layer option of compiz is also off. I tried to disable nautilus as the desktop icon manager, because i thought it was covering the clock, but it isn't. i never see the clock, and when i log out of ubuntu the clock appears when the wallpaper disappears. can anyone help me?

thanks;)

---

### Post by nilarimogard on 2009-06-09
Try using a script to launch them so that they start after compiz starts.

Create a file, let's say 'screenlets.sh' and paste this in it:

```
#!/bin/bash
sleep 20 && command_to_run_each_screenlet
```



(replace 'command_to_run_each_screenlet' obviously). Then:
```
 chmod 775 screenlets.sh
```

And make the file run on startup.

---

### Post by ricardofilipemoreira on 2009-06-15
thanks :) i'll try it

---

