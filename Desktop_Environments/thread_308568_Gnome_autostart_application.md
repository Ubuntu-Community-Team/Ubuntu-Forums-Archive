---
title: "Gnome autostart application"
date: 2006-11-28
forum: Desktop Environments
---

### Post by frkstein on 2006-11-28
Hello,

I would like to know if it is possible to have gnome autostart an application **after** gnome has been fully started.

---

### Post by taurus on 2006-11-28
System -> Preferences -> Sessions -> Startup Programs -> Add!

---

### Post by ciscosurfer on 2006-11-28
> **frkstein said:**
> Hello,

I would like to know if it is possible to have gnome autostart an application **after** gnome has been fully started.Yes.  You can create a script that tells whatever app you want to wait (sleep) until GNOME has loaded.  For example, you can do this```
gedit startgaim.sh
[I]
when gedit opens up, the new file you are creating will be named startgaim.sh

in the file enter the following:
[/I]
#!/bin/bash
#my super duper script
sleep 6  #you can alter the amount of time here
exec gaim #or whatever app you want
```You then need to make the script executable by issuing the following in a terminal (or you can use a GUI too)```
chmod +x ~/startgaim.sh
```Now, under System > Preferences > Sessions > Startup Programs tab, click add and type in ***/home/<your_user_name>/<name_of_script_you_just_created>***

---

