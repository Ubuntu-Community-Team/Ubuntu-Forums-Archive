---
title: "Toggle Compiz Plugins (window decoration) with commands"
date: 2012-08-26
forum: Desktop Environments
---

### Post by Woegjiub on 2012-08-26
Howdy.

Now, it is possible in Kwin to toggle window decoration through the use of a hotkey.
This comes in handy for things like terminals, or vertically maximised windows.

Is there a way to do the same, via setting a command in compiz config to toggle the window decoration plugin, and then to assign a hotkey to this via the next tab over?

The titlebars hide deliciously when a window is maximised, but they are annoying when I have two windows vertically maximised with C_M_left or C_M_right.
Better still would be a way to hide the titlebars when windows are maximised partially in that manner, but I suspect that is not possible.

---

### Post by stinkeye on 2012-08-26
Script to toggle decorations?
```
#!/bin/bash

if pidof /usr/bin/gtk-window-decorator | grep [0-9] > /dev/null
then
	killall /usr/bin/gtk-window-decorator
else
	/usr/bin/gtk-window-decorator
fi
```

---

### Post by Krytarik on 2012-08-26
Just install CompizConfig Settings Manager, if you haven't already, and set "CCSM -> Effects -> Window Decoration -> Decoration Windows" to:
```
!state=maxvert
```Regards.

---

### Post by Woegjiub on 2012-08-26
> **Krytarik said:**
> Just install CompizConfig Settings Manager, if you haven't already, and set "CCSM -> Effects -> Window Decoration -> Decoration Windows" to:
```
!state=maxvert
```Regards.
This is basically exactly what I was looking for, thankyou :D

> **stinkeye said:**
> Script to toggle decorations?
```
#!/bin/bash

if pidof /usr/bin/gtk-window-decorator | grep [0-9] > /dev/null
then
    killall /usr/bin/gtk-window-decorator
else
    /usr/bin/gtk-window-decorator
fi
```

This would come in handy, but killing applications seems somewhat like overkill, when compiz has a means for enabling/disabling plugins, as they are toggleable in CCSM, and seem like they should therefore be mappable to a command, somehow.
If that functionality does not exist, however, your way seems like the quickest and simplest, so thankyou.

---

