---
title: "Can't find X includes."
date: 2005-11-16
forum: Desktop Environments
---

### Post by dmonney on 2005-11-16
Alright, I'm new, so any replies has to be very simple assume I know nothing (cause chances are I don't)

I'm having issues with my wireless card, I can't find any ap's around me, (even though there is my own ap 5 feet from me) I want to be able to just see what ap's are available, like windows so I found out there was the kwifimanager. That couldn't find any c++ compilers, so after hunting for about an hour I found out i can 
sudo apt-get install build-essential
that worked for the most part but now I get a new error.
```

checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for char... yes
checking size of char... 1
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

I looked at a few forums and it said to install a few libraries, that's great but I have no clue how to install libraries. please help

---

### Post by Kyral on 2005-11-16
I think you need xlibs-dev

---

### Post by taurus on 2005-11-16
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install x-window-dev

---

### Post by dmonney on 2005-11-16
alright, I tried your advise taurus, this is what I got.

```
root@Dmonney:/home/derek/Desktop/kwifimanager-1.0.2 # sudo apt-get update
Reading package lists... Done
root@Dmonney:/home/derek/Desktop/kwifimanager-1.0.2 # sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Dmonney:/home/derek/Desktop/kwifimanager-1.0.2 # sudo apt-get install x-window-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package x-window-dev
root@Dmonney:/home/derek/Desktop/kwifimanager-1.0.2 #

```

---

### Post by Kyral on 2005-11-16
Try xlibs-dev

---

### Post by dmonney on 2005-11-16
Kyral,

How do I try xlibs-dev. I'm very new to linux (about a week)

---

### Post by Kyral on 2005-11-16
I meant try installing it (sorry)

Wait a second....kwifimanager is in the repositories you don't need to compile it.

```
sudo apt-get install kwifimanager
```

---

### Post by dmonney on 2005-11-16
Ok so this is what popped back out

sudo apt-get install kwifimanager

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kwifimanager

how do I install xlibs-dev.

---

### Post by Kyral on 2005-11-16
Gak its in Universe. You have to add them (Believe me you DON'T want to compile unless you have to)

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by dmonney on 2005-11-17
thx I did it and it worked great
-D$

---

