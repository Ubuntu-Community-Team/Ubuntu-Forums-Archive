---
title: "Auto-login and graphical login don't work"
date: 2011-04-26
forum: Desktop Environments
---

### Post by cleiton-xavier on 2011-04-26
Hi, I marked the auto-login option when I was doing the installation, but when I finished it and rebooted to start using the system for the first time, not only the auto-login didn't work but I also ain't being capable of logging through the standard graphical  login box, so I have to restart the system in text mode to them enter a "startx" command.
I don't know what it is, because I went to >  System Settings -> User Management - Advanced -> Login Manager - Convenience  and clicked on the "enable auto login" option with my default user name and didn't work. Then i went to /etc/kde4/kdm/kdmrc and saw this:

> [X-:0-Core]
AutoLoginEnable=true so, i don't know why it is not working

No idea also why I cannot login in graphical mode

Thanks for the help

---

