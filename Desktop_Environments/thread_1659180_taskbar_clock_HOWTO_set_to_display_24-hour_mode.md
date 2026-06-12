---
title: "taskbar clock: HOWTO set to display 24-hour mode?"
date: 2011-01-03
forum: Desktop Environments
---

### Post by eltonw on 2011-01-03
Is there a way to change the default clock in the task-bar so that it displays time in 24-hour format, instead of AM / PM?

---

### Post by deanjm1963 on 2011-01-03
Sorry - didn't read the "netbook" part of the post title ...

---

### Post by mycatknowsbetter on 2011-01-03
right click on the clock and go to preferences

---

### Post by kerry_s on 2011-01-03
open a terminal & run "dconf-editor", it will tell you what to install to get it.

---

### Post by eltonw on 2011-01-04
> **kerry_s said:**
> open a terminal & run "dconf-editor", it will tell you what to install to get it.
Yeah: "sudo apt-get install dconf-tools."

It took me a few minutes selecting the check boxes before I found the drop-down menu dialog to switch from 'locale-defualt' to 24-hour. I also elected "show-date" so I niw have the day of the week as well as day of the month.

I usually install things via synaptic or the Ubuntu Software Center, but is is both good practice and a good habit to do things via console commands.

Thank you.):P

---

### Post by batigolix on 2011-08-02
after you run dconf-editor you find the options under Apps > Indicators > Datetime

---

