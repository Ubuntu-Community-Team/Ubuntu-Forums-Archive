---
title: "how to delay sleep mode?"
date: 2010-06-19
forum: Desktop Environments
---

### Post by sea_coffee_programmer on 2010-06-19
when i am working on stuff, i will turn away for like 45 seconds and the screen will be off, and then require me to enter my password.  I know there is a way to delay this action or turn off the password requirement, but i dont know how for linux.  It would be awesome, as it feels that there is more time spent doing passwords then there is actually using the latop at times.

Thanks for your help all!!   =]

---

### Post by kerry_s on 2010-06-19
preferences-> screensaver
preferences-> power manager

alt+f2(if you don't have gconf-editor turned on in the menu)
type: gconf-editor
apps-> gnome-power-manager-> lock
uncheck them all for no password

---

### Post by happyzapp on 2010-09-13
Thanks a bunch. Worked well.
some call me frank

---

