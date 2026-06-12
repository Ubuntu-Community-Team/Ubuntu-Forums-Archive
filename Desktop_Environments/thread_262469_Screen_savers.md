---
title: "Screen savers?"
date: 2006-09-21
forum: Desktop Environments
---

### Post by emm721 on 2006-09-21
i want to know how to get to the advanced settings on screen savers. specifically, the one called "sonar". i remember on the last distro, it allowed me to change settings like the name of the blips, the speed they show ip, density etc. how do i do this on dapper? i checked the help, and nothing was there. well, nothing important.

---

### Post by mgmiller on 2006-09-21
The quick answer is, you can't.  In their infinite wisdom, the Gnome people have removed that function from gnome screensaver.   Search these forums for instructions on how to switch back to x-screensaver, or to at least get the old x-screensaver configuration controls back.  There are many threads here on this topic.

---

### Post by CatKiller on 2006-09-22
> **mgmiller said:**
> The quick answer is, you can't.

Actually, yes you can. Type ```
man sonar
``` into a terminal to see what the options are to do what you want to the configuration. Then ```
gedit /usr/share/gnome-screensaver/themes/sonar.desktop
```will open the configuration file that gnome-screensaver uses for the Sonar theme. There is a line that says > Exec=sonar -rootChange this line to reflect the options that you want.

---

