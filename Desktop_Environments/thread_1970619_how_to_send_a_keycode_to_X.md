---
title: "how to send a keycode to X?"
date: 2012-05-01
forum: Desktop Environments
---

### Post by iBART on 2012-05-01
source of discussion: [http://ubuntuforums.org/showthread.php?p=11894568#post11894568](http://ubuntuforums.org/showthread.php?p=11894568#post11894568)

*how to send a keycode to X?*

12.04 here! thanks :)

---

### Post by iBART on 2012-05-02
up? :(

---

### Post by LewisTM on 2012-05-02
Install xdottool
Then execute for example
```
xdotool key F5
```
Done!

---

### Post by iBART on 2012-05-03
thanks but i need to "send" F5 to desktop to refresh it but xdotool sends "F5" to... itself! :(

---

### Post by LewisTM on 2012-05-03
Well it depends what captures the key and which application is focused when invoking the command. Are you using this as a keyboard shortcut?

What could help you switch to the target window is wmctrl.
A command like this would call the command interpreter, switch to the desktop, wait a fraction of a second for it to come into focus, and send an F5.
```
sh -c "wmctrl -a Desktop && sleep 0.1 && xdotool key F5"
```

---

### Post by iBART on 2012-05-03
**worked!** thanks man. i added it to startup :)

---

