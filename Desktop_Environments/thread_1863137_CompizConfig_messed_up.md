---
title: "CompizConfig messed up"
date: 2011-10-17
forum: Desktop Environments
---

### Post by katchoo85 on 2011-10-17
Today, while i was using CompizCOnfig I accidentally changed my profile. When i clicked on the drop-down menu, it made the log out and from that moment i have no more gnome, just nautilus. So I don't have any launcher and the bar on the top of my desktop only shows the nautilus commands (File, Edit, View, etc.).

On Ubuntu Tweak i noticed that "gnome-wm" is set as windows manager, but when i tried to open it thru the terminal it says that it is not installed. SO i guess that the problem is that i accidentally set as profile something that does not exist on my computer.

What should i do know?

I tried to set compizconfig back to "predefined", but nothing happened. 

What should i do know?

---

### Post by areeda on 2011-10-17
I have had lots of problems with CompizConfig.  It seems anything I do kills Unity.

For me dropping to a login prompt and doing

unity --reset

gets me back.

Others have recommended

gconftool-2 --recursive-unset /apps/compiz-1

one of those might work for you.

Joe

---

### Post by katchoo85 on 2011-10-17
Unfortunatly I already tried both, but nothing changed. 

When I run "unity --reset" at the beginning it says "no process found", and after a while it stucks on this line: "Initializing session options...done"

---

### Post by bobsageek on 2011-10-17
I had the same issue when tinkering with CompizConfig and getting Sandy Bridge 2 acceleration working. Log out, at the log in menu switch to Unity 2D, start CompizConfig and it will complain of conflicts in this mode, just close the window, log out and change the mode back to Ubuntu. I believe it rebuilds a settings file, but I'm not sure which one, but it get me back to a working desktop. 

I should have investigated more as I'm sure there's a more elegant way, but it got me back to a fully functional desktop environment. Planning to wait for a CompizConfig update before I try that again.

---

