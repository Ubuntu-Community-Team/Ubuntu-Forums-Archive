---
title: "desktop environment information from command line"
date: 2013-02-22
forum: Desktop Environments
---

### Post by Erik1984 on 2013-02-22
Is there any reliable way to tell which DE someone is using from the command line? I have seen terminal app that give an overview of your system and I wonder how they get information about WM and DE. I would like to know this for writing my own system summary script.

---

### Post by Elfy on 2013-02-22
echo $DESKTOP_SESSION ?

---

### Post by Erik1984 on 2013-02-22
Thanks. For KDE it gives me kde-plasma so that seems alright :p Does it work for XFCE (assuming you are using that) and other DEs like Gnome, LXDE, Cinnamon ?

---

### Post by Elfy on 2013-02-22
it does here - tells me Xubuntu

---

### Post by Cheesemill on 2013-02-22
Output using Cinnamon....
```
rob@arch:~$ echo $DESKTOP_SESSION

rob@arch:~$ 
```

---

### Post by Erik1984 on 2013-02-22
So it's not very reliable unfortunately. Are there any other ways to determine the DE? I could check for the existence of config folders (.kde .xfce ...) in ~ but that says nothing about the current session as one can have many DEs installed at once.

---

### Post by steeldriver on 2013-02-22
if you're only interested in *local* sessions, I wonder if you could just look at what's running in tty7?

```
$ w $USER | awk '$2 ~ /tty7/ {print $7;}'
gnome-session

```

---

