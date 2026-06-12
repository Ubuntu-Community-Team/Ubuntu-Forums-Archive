---
title: "Lubuntu Minecraft McMyAdmin Server Startup Command"
date: 2011-10-16
forum: Gaming &amp; Leisure
---

### Post by IBUA on 2011-10-16
Hey,

I'm trying to set up a minecraft server using McMyAdmin on lubuntu on an old computer.

I've got everything to work so far, but now am trying to get McMyAdmin to start-up on booting.

The command I need is 
```
lxterminal -x sh -c "cd minecraft-server && ./start.sh"
```

I have checked this command works.

However, I am using Lubuntu to lower memory usage (due to using an old computer) and the [guide]("http://www.overclock.net/pc-games/1012514-guide-minecraft-dedicated-linux-setup-guide.html") i'm using is for ubuntu.

Therefore, the instructions to get the command to work on start up doesn't work, as Lubuntu doesn't have the startup manager.

I've tried creating .desktop files and editing the autostart file in /etc/xdg/lxsession/LXDE but i've had no luck.

Can anyone help with this?

Thanks in advance!

---

