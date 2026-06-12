---
title: "Problem with gnome flashback"
date: 2014-08-25
forum: Desktop Environments
---

### Post by JulienDe on 2014-08-25
I installed gnome flashback on 14.04, and I have two possibly related, or possibly distinct problems:  - I inadvertently suppressed the menu bar, and can't find a way to restore it - at the same time I made that mistake and tried to fix it (without success, but I might have made more damage...), the others bars started to behave in a weird manner - they don't show anymore all the letters (for instance "Short_uts")  I reinstalled the OS, but it did not fix these problems, which hence must be related to a file in my /home (which was not formatted by the reinstallation). Which file though, I have no idea...  Thanks for your help!

---

### Post by JulienDe on 2014-08-26
To solve the problem:   dconf reset -f /org/gnome/gnome-panel/ killall gnome-panel  See for further details [http://askubuntu.com/questions/125662/how-to-reset-gnome-panel](http://askubuntu.com/questions/125662/how-to-reset-gnome-panel)

---

### Post by Programmer135 on 2014-08-26
JulienDe's solution should refresh the enviroment, hopefully it lead to some amelioration of the problem?

---

