---
title: "Enlightenment help"
date: 2005-10-24
forum: Desktop Environments
---

### Post by robert-s on 2005-10-24
I installed enlightenment through synaptic, but when I log out and click on the "sessions" menu at the login screen, the only options are gnome, failsafe, terminal etc. What do I do to get enlightenment to appear on the list, edit some configuration file?

---

### Post by Iandefor on 2005-10-24
Open a terminal, type in ```
sudo gedit /usr/share/xsessions/Enlightenment.desktop/
``` and put the following into the file:                                          
```
[Desktop Entry]
 Encoding=UTF-8
 Name=Enlightenment
 Comment=
 Exec=enlightenment
 Icon=
 Type=Application 
```

Taken from [here]("http://ubuntuforums.org/showthread.php?t=54476&highlight=Enlightened+GNOME")

---

### Post by Ampersand on 2005-10-24
You need to make a file containing th following text: 

```

[Desktop Entry]
Encoding=UTF-8
# The names/descriptions should really be better
Name=Enlightenment Session
Comment=Use this session to run Enlightenment as your desktop environment
Exec=enlightenment
Type=Application

```

and save it in /usr/share/xsessions as enlightenment.desktop . 

Next time you log in, it should be an option.

---

