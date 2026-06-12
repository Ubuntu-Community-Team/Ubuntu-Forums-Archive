---
title: "Shortcut not working"
date: 2005-05-25
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-25
I'm trying to put a shortcut to UT2k4 on my desktop. (the installed one no longer works after installing the patch, probably because now I need to run the 64-bit binary to get it to work.) If I make a shortcut in the folder the executable is, it works. However if I move it to my desktop it won't load. If I drag it to the top menu thing it'll try to add it there, but when I click it it doesn't work. Why's the shortcut not working?

---

### Post by Curlydave on 2005-05-26
bump! Surely someone knows how to make *working* shortcuts to executables or can explain why mine don't work.

---

### Post by Knome_fan on 2005-05-26
Hi, I don't know what you are trying to do here exactly, but if I understand you right:

Click on the top panel -> Choose Add to panel -> Choose Customer Launcher and now point command to the command you want to execute.

---

### Post by apollyonis on 2005-05-26
Have you tried putting the full path to the executable in the command line portion of the launcher? I.E. /usr/bin/ark

All you would actually need to do to add an icon on the desktop in Gnome is to right click a blank portion of the screen -> Create Launcher -> type in command with full path in Command -> click OK. You can then drag and drop it to the taskbar to add it there. I can only suspect that since it was patched and a new command was introduced, the link for /usr/bin no longer works. I don't know what the exact command that was introduced, but replace new.com with whatever the command is and old.com with whatever the old command was: 

```
sudo ln -s /ut2004/bin/new.com /usr/bin/old.com
```

---

