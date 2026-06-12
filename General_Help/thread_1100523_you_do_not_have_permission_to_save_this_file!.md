---
title: "you do not have permission to save this file?!"
date: 2009-03-19
forum: General Help
---

### Post by balador on 2009-03-19
hi
i install ubuntu 8.10 and for install ns-2(tool for network simulation)
i try to edit this file :  /etc/apt/sources.list 
but when i try to edit sources.list i see this error : you do not have permission to save this file.
whats my problem and solution?

---

### Post by Kevbert on 2009-03-19
You need to open this file with
```
sudo gedit /etc/apt/sources.list
```

---

### Post by The Cog on 2009-03-19
Press Alt-F2 and enter the command **gksu gedit /etc/apt/sources.list** to edit the file with root priviledges. Always gksu rather than sudo when launching graphical apps.

This might help explain what's going on:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by alaeddine.ouali on 2009-04-19
hi,

I'm seeking for a tutorial to install network-simulator on ubuntu 8.10 using **apt-get** and not manually by downloading .tar.gz
thx to help me if you can.

Ouali.A :)

---

### Post by Nepherte on 2009-04-19
See this thread: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6961652](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6961652)

If you want to use apt-get, basically you have to add [this ppa]("https://launchpad.net/~wouterh/+archive/ppa"), refresh your list with:
```
sudo apt-get update
```
 and install network simulator:
```
sudo apt-get install ns
```

---

