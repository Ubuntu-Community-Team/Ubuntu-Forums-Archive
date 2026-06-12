---
title: "How can I know my System Memory (RAMs)?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Isoss on 2006-07-19
How can I know my System Memory (RAMs) using linux commands and using a graphical interface?

Thanks in advance.

---

### Post by T700 on 2006-07-19
Open a terminal and type:
```
sudo lshw
```
and you'll get that and more.

Paul

---

### Post by Delkster on 2006-07-19
If you want to know the amount of free system memory or other things like that, you can use the Gnome System Monitor (found in the menus at System -> Administration). KDE has its own Information Center or whatever it's called.

On the command line you can find out how much physical memory you have free using the `free' command. It reports the amounts in kilobytes by default but you can get megabytes with the -m switch, like so:
```

free -m

```

These will report the total amount of RAM as slightly less than the true total amount of physical RAM.

---

### Post by AZzKikR on 2006-07-19
Isn't the system monitor a solution too?

---

