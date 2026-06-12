---
title: "Splashy issues"
date: 2009-01-20
forum: General Help
---

### Post by haarvik on 2009-01-20
How do you get this thing to work?  I tried apt-get install, and it installed but gave me the error -2 message.  Installed startupmanager, and same thing.  I can assign a theme, but splashy won't run.  I followed another forum suggestion about getting it from Alioth (sp?) but it has broken dependencies.  I'm using intrepid.  Tried it on hardy and it wouldn't work there either.  Any clues why this thing won't work?

root@ubuntu:~# splashy test
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2

menu.lst:
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=4053a728-96dd-4989-9bf9-7e5d6f83285f ro quiet splash vga=791

---

### Post by haarvik on 2009-01-20
Nobody has issues with splashy...works out of the box for 1,000's of users...I'm the only one with this issue?

---

### Post by Ptero-4 on 2009-02-05
The problem might be on upstart (I also tried to install splashy and it won´t work). Upstart seems to be hardwired to usplash.

---

