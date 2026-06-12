---
title: "Gnome-Schedule command"
date: 2008-07-19
forum: Desktop Environments
---

### Post by TRANQU111TY on 2008-07-19
I have no experience in scripting and all I want to do is to write a command for two tasks in Gnome Schedule- to run Transmission and to shut down the computer at certain times.

For one task in the command box I have used 'transmission' but nothing happens unless I run the task manually. I am not sure how to write a script for the shut down.

---

### Post by pauper on 2008-07-19
```
man at
man cron
man anacron
```

Then go here, for example:
[http://ubuntuforums.org/showthread.php?t=102626&highlight=cron](http://ubuntuforums.org/showthread.php?t=102626&highlight=cron)

---

### Post by spupy on 2008-07-19
> **TRANQU111TY said:**
> I have no experience in scripting and all I want to do is to write a command for two tasks in Gnome Schedule- to run Transmission and to shut down the computer at certain times.

For one task in the command box I have used 'transmission' but nothing happens unless I run the task manually. I am not sure how to write a script for the shut down.

First, open a terminal and type
```
env | grep DISPLAY
```
The output will be something like
```
DISPLAY=:0.0
```
Copy this line. Now, for the shutdown, the command you need is:
```
DISPLAY=0:0 gksu "shutdown -h now"
```
You need to replace the DISPLAY with the one you got from the first command.
For transmission, it is similar:
```
DISPLAY=0:0 transmission
```

Hope this works for you.

---

### Post by phonicboom on 2009-02-01
I could not get Transmission to launch with Gnome Scheduler but found **Deluge** has a plugin that lets you schedule torrent times :)

---

### Post by mister_p_1998 on 2009-02-02
I find ktorrent best for scheduling start stop times. My PC starts at 11:45 pm, Ktorrent starts with Cron at 00:15 and torrents transfer until 18:00. Cron then runs the comand Killall ktorrent.

Steve

---

