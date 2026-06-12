---
title: "cd any directory in terminal from that directory"
date: 2011-04-11
forum: Desktop Environments
---

### Post by harshveer on 2011-04-11
Hi all, I am trying to cd a directory from directory itself. And for that what I have done is:

1. I created a small shell script:
```
#! /bin/sh
gnome-terminal --working-directory = $HOME'/dir1/dir2'
```I placed this script at $HOME/bin/openDirToTerminal.sh
2. I created a launcher and gave command /home/h/bin/openDirToTerminal and placed this launcher in $HOME/dir1/dir2/

All this is working fine. 
But problem is that I have to write different scripts for different directories and create launcher for these scripts. Isn't there any way to create a single script and place launchers for this script in different directories. May be like when launcher is triggered it  sends path of its existence to the script and script cd that path to terminal.
Thanks.

---

### Post by mcduck on 2011-04-11
Just install the *nautilus-open-terminal* package and you'll get an option to open a terminal in current directory in your right-click menu.

---

### Post by harshveer on 2011-04-11
thanks, it is helpful.

---

