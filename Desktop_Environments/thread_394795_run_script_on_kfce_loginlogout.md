---
title: "run script on kfce login/logout"
date: 2007-03-27
forum: Desktop Environments
---

### Post by danl on 2007-03-27
I'm running Xubuntu 6.10. I'm trying to get a bash shell script to run when a user logs into the desktop. The script runs fine from a terminal window. I've tried:

-adding an entry using Settings->Autostarted Applications that points directly to the script

-putting a soft link directly in ~/.config/autostart to the shell script

Neither worked. Perhaps autostart is only for GUI apps or executables?

I don't want this script run as part of system startup or bash login. Has anyone been successful doing this? If I get it to run at login, I'd also like a script run at logout as well.

thanks,
dan

---

### Post by x1a4 on 2007-03-27
Hi,

~/.config/autostart/ holds .desktop files.  

Create this text file: 

~/.config/autostart/name-of-myscript.desktop

and edit it like so: 

[Desktop Entry]
Exec=/path/to/name-of-myscript
Terminal=true

---

### Post by danl on 2007-03-27
Thanks. That works.

---

