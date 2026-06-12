---
title: "Unity launcher mouse click minimize and maximize?"
date: 2014-06-18
forum: Desktop Environments
---

### Post by serouj2 on 2014-06-18
i was wondering if anyone here can tell me if its possible to use your mouse wheel-down to minimize and it already has the function of mouse wheel up maximize ....i want to use it like a taskbar and not go to the side and click minimize every darn time ...any ideas or installations or anything?

---

### Post by deadflowr on 2014-06-18
Moved to Desktop Environments

---

### Post by grumblebum2 on 2014-06-19
You probably don't want to use your scroll button for this.
Have a look at **easystroke** mouse gestures.

Set a gesture for maximize and minimize using an existing keyboard shortcut and a wmctrl command.

```
sudo apt-get install easystroke wmctrl
```

This wmctrl command will toggle a focused window maximized/unmaximized...
```
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
```

Set the wmctrl command to a gesture and your minimize shortcut key to another gesture.
In easystroke preferences I change the gesture button to 3 (right click) as I find that more natural.

The beauty of using easystroke is you can bring a familiarity to any desktop environment or installation.
Just need to copy over your  **~/.easystroke** folder.

---

### Post by serouj2 on 2014-06-19
no i want to use mouse

---

### Post by grumblebum2 on 2014-06-19
You can also bind mouse buttons to commands and keyboard shortcuts with easystroke.

Not sure if your aware or not but you can also enable minimize click for launcher icons in 14.04.
Terminal...
```
gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true
```

---

### Post by serouj2 on 2014-06-19
finally no i wasnt aware of that but finally i found something XD thanks ...

---

