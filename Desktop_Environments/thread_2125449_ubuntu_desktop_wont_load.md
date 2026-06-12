---
title: "ubuntu desktop wont load"
date: 2013-03-14
forum: Desktop Environments
---

### Post by benhorton2 on 2013-03-14
I was running ubuntu 12.04 LTS and it automatically updated. When it booted, i got the command line login prompt. I used my username and password and then used startx to run the GUI. However, only the desktop and mouse loaded, none of the other features of gnome desktop. I am able to use ctrl-alt-t and cairo-dock to get by, but I would like to have a fully functioning desktop. Any help would be greatly appreciated.

---

### Post by carl4926 on 2013-03-14
Graphics driver?

---

### Post by Frogs Hair on 2013-03-14
Try Ctrl +Alt +T ```
unity --reset
```

---

### Post by benhorton2 on 2013-03-15
thanks, that did the trick. but whenever i restart the computer it goes to the command line and i have to manually startx and then unity --reset. Is there any way to make these things happen at boot?

---

