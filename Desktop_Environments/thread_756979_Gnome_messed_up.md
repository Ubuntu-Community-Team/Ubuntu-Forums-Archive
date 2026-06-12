---
title: "Gnome messed up"
date: 2008-04-16
forum: Desktop Environments
---

### Post by drmoore1 on 2008-04-16
I was doing an update and had tried to add a program to my system bar up-top. The computer then froze and I had to hard restart and now it says gnome power manager is not installed correctly. All the menus on the top panesl are missing icons and the graphics of firefox are messed up.  All the graphics look like its a system from 10 years ago or windows in safe mode somewhat. Also when I start ubuntu, it does a routine check of the drives and hangs up everytime unless I skip this.

---

### Post by Diabolis on 2008-04-16
The update that you were doing didn't finish.

go to here system / synaptic package manager / edit / fix broken packages

Something similar happened to me while upgrading the kernel. I fixed it by booting from a live-cd and issuing this commands at terminal:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by drmoore1 on 2008-04-17
ok cool, thank you

---

