---
title: "run as priviliged user"
date: 2006-04-01
forum: Desktop Environments
---

### Post by wshamroukh on 2006-04-01
Hi all

i want to run the add remove programs using a priviliged user ther than the root.. how can i do this... i tried to run this tool from /usr/bin/gnome-app-install but i got errors... any body can help here

---

### Post by Sutekh on 2006-04-01
Root is the only privileged user who can run that sort of task.

An ordinary user *can* be allowed to run the program as root using **sudo** (Apologies if you already know this)  See [Ubuntu Wiki - RootSudo](wiki.ubuntu.com/RootSudo)

```
sudo gnome-app-install
```
or```
gksudo gnome-app-install
```
Will work, but require you user password to run the application.

---

