---
title: "Restart X-server"
date: 2009-10-29
forum: Desktop Environments
---

### Post by b4k4 on 2009-10-29
UNR 9.04, there is no "restart x-server" on the login page menu and ctrl-alt-backspace doesn't work.

Anyone know why? Or more importantly, how to fix it?

cheers
nigel

---

### Post by rabidbadger on 2009-10-30
I don't use UNR, but I guess that it's set up the same as other 9.04s?

If so, you can re-enable <ctrl><alt><bksp> by editing your xorg.conf, and diasabling *DontZap*. You can do this from a Bash prompt by copy/pasting (as a complete three line block) the code below. HTH.

```
sudo sed -i '$a\Section "ServerFlags"\
Option "DontZap" "False"\
EndSection' /etc/X11/xorg.conf
```

---

