---
title: "StumpWM: no mouse, no keyboard"
date: 2013-06-17
forum: Desktop Environments
---

### Post by JakubLedl on 2013-06-17
Hello everybody,

after setting up a StumpWM desktop, I'm facing a problem: when I try to autologin to the StumpWM session, neither the mouse or keyboard work (I can only Ctrl-Alt-F1 to a terminal). This is the .desktop file I'm using:

```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=default
Name=StumpWM

```

xsession contains only [FONT=courier new]exec stumpwm[/FONT]. I've tried different combinations of [FONT=courier new]Type=XSession[/FONT] and [FONT=courier new](Try)Exec=stumpwm[/FONT], but without luck.

For the time being, I've simply disabled autologin (when I login to the session from the LM, everything works as it should), but this is somewhat suboptimal solution, so any ideas will be much appreciated :) Thanks in advance!

---

### Post by dino99 on 2013-06-17
Stumpwm has not been updated since nov 2011 :confused:  seems an abandonware  :(
[http://askubuntu.com/questions/101215/stumpwm-as-window-manager](http://askubuntu.com/questions/101215/stumpwm-as-window-manager)

---

