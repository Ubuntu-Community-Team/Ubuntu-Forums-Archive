---
title: "trouble installing ET"
date: 2005-12-30
forum: Gaming &amp; Leisure
---

### Post by Specialsauce on 2005-12-30
it asks me to enter my password when i try to install enemy territory, but then it gives me this weird error:
[IMG]http://xs61.xs.to/pics/05525/Screenshot-1.png[/IMG]

---

### Post by Zimmer on 2005-12-30
[QUOTE=Specialsauce]it asks me to enter my password when i try to install enemy territory, but then it gives me this weird error:
[/QUOTE]
Try downloading and installing Et 2.6..
See the wiki here for installation tips,including troubleshooting permissions
ie:
Permission Errors

Change the permission with this command:

sudo chmod +x et-linux-2.60.x86.run
sudo chmod +x et-linux-2.60-update.x86.run


[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)
regards

---

### Post by fordfan753 on 2005-12-30
It asks you to enter your **root** password...Just make sure you didn't enter your **sudo** password, hint: they are different, and you will have to set a root password because Ubuntu isn't Debian

---

### Post by Specialsauce on 2005-12-30
how do i set a root password

---

### Post by fordfan753 on 2005-12-30
Pop up a terminal, then simply type:
```
sudo passwd root
```
It'll ask you for a password, enter your sudo password, it will then ask for another password, this will be the one you want to set for the root account, then it'll ask you to confirm the root password.

---

### Post by Zimmer on 2005-12-31
[QUOTE=fordfan753]Pop up a terminal, then simply type:
```
sudo passwd root
```
It'll ask you for a password, enter your sudo password, it will then ask for another password, this will be the one you want to set for the root account, then it'll ask you to confirm the root password.[/QUOTE]
I am pretty certain You do NOT need to do that to install ET....I can't remember doing it...I followed the wiki as per my last post...

---

### Post by Luzbel on 2005-12-31
You just need to type:

$ sudo sh et*run

---

### Post by ulisse on 2006-01-01
You can hit "cancel" when asked for root password, the game will be installed in your home dir instead of /usr/local/games.
If you need/prefer you can still move there the enemy-territory dir by hand, after the install, or simply create a symlink to the executable.

---

