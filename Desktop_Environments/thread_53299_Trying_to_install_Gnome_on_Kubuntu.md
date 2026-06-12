---
title: "Trying to install Gnome on Kubuntu"
date: 2005-07-31
forum: Desktop Environments
---

### Post by gordonbp on 2005-07-31
I originally installed Kubuntu, and it's great. However I HATE Knode for news! So I want to install the Gnome desktop as it has Pan in it. I used the following command in a terminal:
sudo apt-get install ubuntu-desktop

and got the error message "couldn't find package ubuntu-desktop".
What am I doing wrong?

---

### Post by SGC on 2005-07-31
There is no need to install ubuntu to use pan, all you have to do is running this command:
sudo apt-get install pan

---

### Post by gordonbp on 2005-07-31
[QUOTE=SGC]There is no need to install ubuntu to use pan, all you have to do is running this command:
sudo apt-get install pan[/QUOTE]
 I get the error:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package pan

---

### Post by Buffalo Soldier on 2005-07-31
Have you tried:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install pan
```
How about sharing your */etc/apt/**sources.list*** file?

---

