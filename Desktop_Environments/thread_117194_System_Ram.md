---
title: "System Ram?"
date: 2006-01-14
forum: Desktop Environments
---

### Post by SuperMike on 2006-01-14
I give up and the Ubuntu "help" (if you can call it that) on the Ubuntu Start Menu doesn't help. What command or menu choice do I pick to find out how much onboard system RAM I have? I need to get more because Ubuntu 5.10 and/or the applications I tend to use (PostgreSQL, Apache, GNOME, Mozilla, PHP, Screem) are memory hogs.

---

### Post by art on 2006-01-14
You mean like 
gnome-system-monitor
 or
free -m

---

### Post by SuperMike on 2006-01-14
[QUOTE=art]You mean like 
gnome-system-monitor
 or
free -m[/QUOTE]

Yep, that's it! :)

Thanks!

---

### Post by dcstar on 2006-01-14
[QUOTE=SuperMike]Yep, that's it! :)

Thanks![/QUOTE]
And if you want to see what RAM resources you have on your system:

lshw

And look for the Memory section........

---

