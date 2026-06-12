---
title: "[SOLVED] X Display Won't Register for Crontab Wallpaper Script"
date: 2008-08-28
forum: Desktop Environments
---

### Post by mikegmcb on 2008-08-28
My friend designed a script to change the wallpaper randomly from a folder of given .jpgs using FEH, but trying to run it as a Cron operation doesn't seem to work.

My crontab looks like this:
```
#
* * * * * DISPLAY="localhost:0.0" /home/user/setbackground.sh
```

When I put this command in the terminal, however... I get this error...
```
user@user:~$ DISPLAY=localhost:0.0 /home/user/setbackground.sh 
feh ERROR: Can't open X display. It *is* running, yeah?

```

Any ideas as to why X won't work when it's under DISPLAY=localhost?

---

