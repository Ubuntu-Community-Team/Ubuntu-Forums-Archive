---
title: "Executing commmand before X boot."
date: 2006-07-07
forum: Desktop Environments
---

### Post by TheMono on 2006-07-07
I'm wondering, is it possible to have a prompt in Ubuntu's boot process to execute a single command - specifically, is it possible to have it ask:

"1 monitor or 2?"

and if 2, execute 
sudo cp /etc/X11/xorg.conf.multimonitor /etc/X11/xorg.conf
gconftool-2 -t str --set /apps/panel/toplevels/panel_2/orientation "bottom" && gconftool-2 -t int --set /apps/panel/toplevels/panel_2/monitor "1"

and if 1, execute 
sudo cp /etc/X11/xorg.conf.singlemonitor /etc/X11/xorg.conf
gconftool-2 -t str --set /apps/panel/toplevels/panel_2/orientation "right" && gconftool-2 -t int --set /apps/panel/toplevels/panel_2/monitor "0"

I've already got the xorg.conf's set up, and I already use this as a script after launch and then restart X, but I'm wondering if it is possible before X is started.

I'm certainly not a programmer though.

---

