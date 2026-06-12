---
title: "i can not install gnome shell in ubuntu 12.4"
date: 2012-11-06
forum: Desktop Environments
---

### Post by iyasin on 2012-11-06
hi all, 
i am traying to install gnome-shell, i follow this tutor:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell
```when i run ```
sudo apt-get install gnome-shell
``` below error apear for me:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[B]The following packages have unmet dependencies:
 gnome-shell :[/B] [B]Depends: gnome-icon-theme-full but it is not going to be installed
E: Unable to correct problems, you have held broken packages[/B]. 
```tnx all

---

### Post by Cheesemill on 2012-11-06
You don't need to add the Gnome PPA to install gnome-shell, try removing the PPA by deleting its files in the /etc/apt/sources.list.d/ directory and then running:
```
sudo apt-get update
sudo apt-get install gnome-shell
```

---

### Post by iyasin on 2012-11-09
tnx all for reply to this thread,
my problem was solved with update ubuntu in update manager, i am active importanant and recomened update in update manager, so it recomend me aproximatly 130 Mb of update, and after update them, that command for install gnome shell work well.

---

