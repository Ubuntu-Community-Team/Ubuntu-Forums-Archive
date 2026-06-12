---
title: "Desktop will not load"
date: 2018-04-04
forum: Desktop Environments
---

### Post by RobGoss on 2018-04-04
Hello all im running 16.04 with gnome  and today when I loaded my desktop only the background shows nothing else

Not sure what's wrong

Thanksgiving for any help with this

---

### Post by Frogs Hair on 2018-04-04
Do you have terminal access via the desktop context menu ? If so try the following. ```
gnome-shell --replace
``` You may also be able to run the command in TTY (ctrl + alt + F1) and return using ctrl  + F7.

Edit: Another alternative is ctrl+ alt+ F2 and this could offer a command option depending on shell version.

---

### Post by RobGoss on 2018-04-04
Thank you  Frogs Hair, I don't know what happen but after playing around at the login screen I believe I upgraded from 16.04 to 18.04 some how so I just changed the desktop ENV at login and was able to see my files and apps that I had installed

---

