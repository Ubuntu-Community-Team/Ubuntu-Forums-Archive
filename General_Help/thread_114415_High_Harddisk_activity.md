---
title: "High Harddisk activity"
date: 2006-01-08
forum: General Help
---

### Post by grussmir on 2006-01-08
Hi,

I installed Kubuntu 5.10 on my Laptop.
Now the Harddisk shows activity, while I m not doing anything.
Seems to access the HD every second or so, the HD never gets quiet.
What going on with my machine???

Thank you for answering 

Michael

---

### Post by pelle.k on 2006-01-15
I dont want to sound so harsh, but did you even bother to do a search on this issue?
"hd activity" spawned some threads on the this subject...

Anyway:
"sudo laptop-mode start" should do it.

It was written to save battery life on laptops, using memory to cache things a while before being written to disk. I suppose syslogd and other deamons regurarly dump logs to hd and stuff. laptop-mode works really well with desktop computers as well.

Add it to autostart menu (kde), or sessions menu (gnome). Or you can make it start at runlevel by:

create the file with nano
"sudo nano -w /etc/init.d/laptopmode"

edit the file like this
```

#!/bin/sh
laptop-mode start
```
Control+o to save it.

make it executable
"sudo chmod +x /etc/init.d/laptopmode"

add a link to a runlevel
"sudo ln -s /etc/init.d/laptopmode /etc/rc2.d/S99laptopmode"

from official faq:
How do I check if laptop mode is enabled?
Do "cat /proc/sys/vm/laptop_mode". If it contains a nonzero value, then laptop mode is enabled, if it says 0, then it isn't.

Good luck :)

---

