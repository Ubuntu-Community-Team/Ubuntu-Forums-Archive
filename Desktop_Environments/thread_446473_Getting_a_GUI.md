---
title: "Getting a GUI"
date: 2007-05-17
forum: Desktop Environments
---

### Post by Bobscrachy on 2007-05-17
I just installed Ubuntu server edition 7.04 on a spare laptop i just got recently. I'm a new convert to linux and i was able to install it, but im not familiar with the bash prompt. After installation thats what i get. I logged in and I don't know how to bring up the GUI. Is there some tutorial or howto for new converts that are spoiled on the windows environments?

Thank you, 
~Bob

---

### Post by taurus on 2007-05-17
If you installed the server version of Feisty, then all you have is a console, no GUI.  If you want a window manager, then you need to install it.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by jediborger on 2007-05-17
In the server install there is no gui. But it's not hard to install one. Again you have lots of choice but since it's a server you'll probably want something small so here's what I recommend. For installing packages you type 
```
sudo apt-get install <package name>
```
So for a basic windowmanager:
```
sudo apt-get install xorg icewm menu gdm
```
If you want firefox, thunderbird, or any other gui goodies that you miss, just add them to the list and afterwards when you restart you should get the usual login with gdm.

---

### Post by Bobscrachy on 2007-05-17
Thank you guys, it looks like its working. Its been loading default applications for awhile now. Is there a place with a list of most used commands and bash syntax?

---

### Post by pebo on 2007-05-17
Try [this]("http://rute.2038bug.com/index.html.gz") tutorial

---

### Post by RedSquirrel on 2007-05-18
The guides at the linux documentation project are another option:

[www.tldp.org](www.tldp.org)

---

