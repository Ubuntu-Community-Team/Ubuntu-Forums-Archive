---
title: "Display Won't Wake"
date: 2022-03-08
forum: Desktop Environments
---

### Post by steffancline on 2022-03-08
Running Ubuntu Server 21 with the Ubuntu Gnome Desktop installed. When the server boots up, I see the GUI user picker. After a few minutes the screen goes black as expected. Moving the mouse or pressing any key on the keyboard will not wake the display and show the user list again. I can do the control alt F1 to get the textual user login but not the GUI user list. If I do a killall gdm3 from the terminal, the user list comes right back up. 

Anyone seen a fix for this?

---

### Post by pissedoffdude on 2022-03-18
Mind reproducing the issue, taking note of the exact time it occurs at, restarting gdm3, then getting us a copy of:

1) sudo lspci -v > lspci.txt
2) A copy of /var/log/syslog
3) A copy of /var/log/kern.log

Best,
Gabe

---

