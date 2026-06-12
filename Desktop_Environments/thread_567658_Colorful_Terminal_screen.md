---
title: "Colorful Terminal screen"
date: 2007-10-04
forum: Desktop Environments
---

### Post by cajunlibra on 2007-10-04
Does anyone know of a terminal-like app that works exactly like the terminal but highlights the "root@user: /home/user" so that it's easy to find when scrolling?


Thanks

---

### Post by T700 on 2007-10-04
Maybe I misunderstood your question, but if you just want to make the typing easier to read, you could go to the settings and then the configuration menu and change the font size and/or color.  I like a nice, hot, green, myself.

Paul

---

### Post by pedrogl on 2007-10-05
```
gedit $HOME/.bashrc
```
and append the following at the end:
```
PS1="\[\e[1;31m\][\u@\h: \[\e[1;34m\]\w\[\e[1;31m\]] $ \[\e[0m\]"
```

look [here]("http://www.ibm.com/developerworks/linux/library/l-tip-prompt/") for more options.

---

