---
title: "mouse is MIA!"
date: 2015-12-02
forum: Desktop Environments
---

### Post by cowboy3 on 2015-12-02
ok so ive searched and searched for a solution, but so far the [COLOR=#111111][FONT=Consolas]"[/FONT][/COLOR]gsettings set org.gnome.settings-daemon.plugins.cursor active false" hasnt worked. im trying to figure out what other methods there may be for fixing this issue. the mouse is present but invisible, i can right click menu my way around the screen but it is really hard.  this is a fresh install, should i just reinstall?  is it worth trying to fix, there only seems to be one workaround and its not working for me, so im thinking its time to branch to a different distro.  suggestions in either direction would be appreciated...
edit: afterthought= lubuntu 15.04, last night i tried installing the amd drivers, for my a10 apu and when i got on it this morning it had finished but only the top left quadrant of my screen had visible desktop and mouse but was completely unresponsive couldnt even pull a terminal up. restarted, have the cpu and update part of the drivers working and selected, but  the mouse is gone again.

---

### Post by vasa1 on 2015-12-02
> **cowboy3 said:**
> ok so ive searched and searched for a solution, but so far the **"gsettings set org.gnome.settings-daemon.plugins.cursor active false"** hasnt worked. ...
Where did you find that?
All I have is```
org.gnome.desktop.interface cursor-blink-timeout 10
org.gnome.desktop.interface cursor-theme 'Adwaita'
org.gnome.desktop.interface cursor-blink-time 1200
org.gnome.desktop.interface cursor-blink true
org.gnome.desktop.interface cursor-size 24

```but this is on Lubuntu 14.04 LTS.

---

### Post by cowboy3 on 2015-12-02
google lubuntu 15.04 invisible mouse and nearly every link on that first page contains that suggested fix.
[http://askubuntu.com/questions/626078/mouse-cursor-invisible-after-15-04-update](http://askubuntu.com/questions/626078/mouse-cursor-invisible-after-15-04-update)
has a bunch of different things but so far no luck.

---

### Post by JonoBNZ on 2015-12-18
Did you ever get a result with this?  I've been able to make mine come back by opening a terminal window and restarting lightdm, as suggested, on restart.

Not really an 'elegant' solution, though.

---

