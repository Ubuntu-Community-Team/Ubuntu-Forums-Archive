---
title: "&quot;move to workspace&quot; option not available on maximized window"
date: 2013-02-03
forum: Desktop Environments
---

### Post by abulawa on 2013-02-03
In Ubuntu 12.04, the "move to workspace" option appears by clicking on the title bar of a non-maximized window.   However, it is not available by right clicking on the title bar of a *maximized* window.

Is this a bug?  Is there a workaround?

I'm aware that the keyboard shortcut Alt-space will bring up the option, but I was hoping to find a mouse-only solution.

---

### Post by ibjsb4 on 2013-02-03
You may want to look into Devilspie.

[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

---

### Post by stinkeye on 2013-02-03
Install xdotool and use ccsm (compizconfig-settings-manager) to set the command
```
xdotool key alt+space
```
to be initiated when you click the top of the screen with right mouse.

---

### Post by zombifier25 on 2013-02-04
> **stinkeye said:**
> Install xdotool and use ccsm (compizconfig-settings-manager) to set the command
```
xdotool key alt+space
```
to be initiated when you click the top of the screen with right mouse.

That's a pretty neat trick. Thanks!

---

### Post by abulawa on 2013-02-05
> **stinkeye said:**
> Install xdotool and use ccsm (compizconfig-settings-manager) to set the command
```
xdotool key alt+space
```
to be initiated when you click the top of the screen with right mouse.
Thank you!  That works very well!

---

