---
title: "Panel Menus Don't Exist"
date: 2011-09-11
forum: Desktop Environments
---

### Post by NattyNoobCake on 2011-09-11
I'm using ubuntu 11.04 (not wubi) 64-bit
when i enter Ubuntu classic through the login screen, everything seems fine...
..until i try to customize the panels in the desktop. When i right click on an empty space on a panel, I only see two options: "help" and "about panels"

Can someone tell me how to get past this so I can move/delete panels again?

---

### Post by JRV on 2011-09-11
It sounds like the panels may be locked.

To unlock the panels:

Open Configuration Editor with the command:
 
```
gconf-editor
``` 

Then browse to apps/panel/global and unmark the 'locked_down' key.

---

### Post by NattyNoobCake on 2011-09-11
best help ever
thank you!

---

