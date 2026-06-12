---
title: "How to get rid of XDG user directories"
date: 2020-09-09
forum: Desktop Environments
---

### Post by nunchuks on 2020-09-09
So I restricted snap permission to home, and some apps have recently tried to get past that by using xdg-user-dirs, xdg-utils etc to copy everything in my home directory into the snap folder when I use that snap. 

I can't save changes into the ".config" txt file, unlike what it says. 

I have tried uninstalling ad purging every xdg package in Terminal, but xdg-user-dirs-update still runs. How do I change that? eg) set Dummy path? :confused:

---

### Post by TheFu on 2020-09-10
What about removing all snaps and the snapd package? Seems like the root cause for the problem described.

---

