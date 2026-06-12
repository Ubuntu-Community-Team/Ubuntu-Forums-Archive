---
title: "where are the gnome start-up apps specified?"
date: 2006-11-30
forum: Desktop Environments
---

### Post by kakyoism on 2006-11-30
Hi, 

My gnome crashed probably because of the startup app "scim -d"

Can anyone let me know which config file specifies the starup program for gnome??

Thank you very much!

Beinan

---

### Post by dbott67 on 2006-11-30
Some can be found in **SYSTEM > PREFERENCES > SESSIONS**
Just click on the "Startup Programs" tab.

If there's nothing there, try looking in **/etc/rc.local**:
```
cat /etc/rc.local
```
```
dbott@edgy:/etc$ cat rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
dbott@edgy:/etc$ 

```

-Dave

---

### Post by CatKiller on 2006-12-01
If you can't log in graphically, some entries that you put in the Session startup screen are kept as .desktop files in ~/.config/autostart. You could use a virtual console (**Ctrl-Alt-F2**) to log in and delete them from the command line. Then use **Alt-F7** to get back to the graphical login screen.

---

