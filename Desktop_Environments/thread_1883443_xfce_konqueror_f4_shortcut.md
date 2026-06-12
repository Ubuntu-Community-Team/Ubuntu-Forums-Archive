---
title: "xfce konqueror f4 shortcut"
date: 2011-11-19
forum: Desktop Environments
---

### Post by xu-leo on 2011-11-19
My system is xubuntu-10.10 on a Lenovo T61 laptop. This is my frist post in this forum.

For navigating in my file system i use konqueror from the keyboard and the f4 short cut to open a terminal in the actual directory konqueror is set to.

Being a kde program konqueror's f4 shortcut opens konsole as terminal.

Does anybody know how i can change this to xfce4-terminal?

I searched all config files for konqueror i could 'locate' on my system but didn't see any setting for the f4 shortcut.
In the Konqueror handbook the use of the f4 shortcut is shortly mentioned but nothing said about changing the behaviour.

Any ideas?

TIA

Hellmut

---

### Post by 3Miro on 2011-11-19
Konqueror is a KDE program and hence the default terminal is probably set using KDE System Settings. I am not sure where exactly.

---

### Post by a.sarkar on 2012-06-10
Sorry to resurrect an old thread. But I found the answer to OP's question and thought I would share the answer.

```
sudo apt-get install systemsettings
```Then type the command systemsettings in a terminal and follow the directions below:

```
systemsettings > Workspace Apperance and Behaviour > Default Applications 
    > Terminal Emulator > Use a different terminal program:
    > xfce4-terminal
```

---

