---
title: "programs in startup"
date: 2007-04-25
forum: Desktop Environments
---

### Post by mitjab on 2007-04-25
I add program to startup but when i close it and reopen it there is no program in startup anymore. Any idea why?

---

### Post by elchato on 2007-04-25
...don't want to hijack anything... but how do you add programs on startup?

---

### Post by mitjab on 2007-04-25
system->settings->session

---

### Post by leashy on 2007-04-27
> **mitjab said:**
> I add program to startup but when i close it and reopen it there is no program in startup anymore. Any idea why?

The same thing is happening to me. I add gDesklets to Session-Startup Programs. If i then reopen it, its gone. I also cant make any changes to whats already in there. If i uncheck something, when i go back in it is checked again. Very annoying. Anybody else experience this or have a solution?

---

### Post by Aetherius on 2007-04-27
make .desktop files linking to what you want to start up and put them in 

/home/username/.config/autostart/

For those who don't know how to make a desktop file do the following.

open up a terminal and type

> nano ~/.config/autostart/name_of_application.desktop

in the nano window put the following

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name[en_GB]=NAME_OF_APPLICATION
Exec=path_to_executable
X-GNOME-Autostart-enabled=true


```

path_to_executable will be whatever you type in the terminal to start the app, eg 'gdesklets' or '/usr/bin/gdesklets'

then hit ctrl+x     type 'y'     and hit enter

log out and in

---

### Post by leashy on 2007-04-27
I found the fix here. Works perfectly.

[http://ubuntuforums.org/showthread.php?t=286883]("http://ubuntuforums.org/showthread.php?t=286883")

---

