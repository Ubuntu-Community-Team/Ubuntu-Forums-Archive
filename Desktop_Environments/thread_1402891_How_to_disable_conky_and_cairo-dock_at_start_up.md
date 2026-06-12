---
title: "How to disable conky and cairo-dock at start up?"
date: 2010-02-09
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-09
Hi,
i installed conky and cairo-dock on my dell mini 10v. Then i made little script to activate external display and after that conky and cairo-dock-so that they can be shown properly on my external display if it is plugged in (otherwise, after each reboot i have messed up display)
```
#!/bin/sh
xrandr --output LVDS1 --off --output VGA1 --mode 1366x768 --pos 0x0 --rotate normal
conky
cairo-dock -c
```

Still, although i disabled in startup/sessions conky and cairo-dock (even deleted them) they are showing again and again (cairo-dock with popup window, as by the first start up). So i have multiple instances of conky and cairo-dock running.

So, it looks, like xubuntu has memorized initial running/startup of conky and cairo-dock, and it starts it again and again after reboot.

I want only to have my startup disk in sessions.

Any clue on this?

---

### Post by vickoxy on 2010-02-09
.xsession-errors are really showing conky and cairo-dock starting with multiple errors although they are disabled in startup.

---

### Post by vickoxy on 2010-02-09
I reinstalled cairo-dock and conky, but the behaviour is exactly the same-as initial cairo-dock startup with the opengl window pop up really deep in xfce session memorized is.
Is there any .sh startup file/script where can i check if it maybe stays cairo-dock or conky?

---

### Post by vickoxy on 2010-02-09
Workaround: i changed my startup script:
> #!/bin/sh
sleep 1 && killall cairo-dock
xrandr --output LVDS1 --off --output VGA1 --mode 1366x768 --pos 0x0 --rotate normal
conky &
sleep 5 && cairo-dock -c

Now i killed that initial cairo-dock start, and after screen switching i have no pop up window.

Still, this is only workaround-and i have no idea why i can not kill that cairo-dock at start?

---

### Post by vickoxy on 2010-02-11
Before reboot needed to kill cairo-dock and conky, then to save session. After that i add to startup my script, and now everything works just fine.

---

