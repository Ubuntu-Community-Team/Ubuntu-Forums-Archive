---
title: "Hardy KDE4 KDM Login Crash"
date: 2008-05-17
forum: Desktop Environments
---

### Post by xevix on 2008-05-17
Just installed Hardy last night, left it suspended to RAM (which I tested and it seemed to work).  It wouldn't come out of suspend after 5 minutes, so I did a hard poweroff.  Then I tried loading normally, but kdm wouldn't come up and stuck me in a TTY.  I loaded kdm manually, and it loaded.  I tried to login, but then kdm crashed out.

X by itself will load, and mouse can move.

kdm.log had this to offer:

```
May 17 10:04:35 dyphaestus kdm_greet [6527]: Cannot read from core
May 17 10:04:35 dyphaestus kdm [6512]: Unknown session exit code 0 (sig 6) from manager process
```

And nothing out of the ordinary in Xorg.log as far as I can tell.

---

### Post by xevix on 2008-05-17
Well, upon reboot, this time kdm.log gave a useful hint.  Turns out that the fingerprint reader, and telling PAM to use it, was causing PAM to crash kdm every time I tried logging in, so I disabled it (thinkfinger).  I'm going to give fprint a shot later and hopefully it's more reliable...

---

