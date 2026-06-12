---
title: "Unwanted Abiword"
date: 2015-05-30
forum: Desktop Environments
---

### Post by kmand on 2015-05-30
Suddenly I get an Abiword window on my desktop when I login. This is on Ubuntu 15.04 (unity), which I believe showed up after an upgrade from 14.04.

There is no Abiword (or anything like it) in "Startup Applications Preferences". How do I keep it from starting up on login?

---

### Post by egeezer on 2015-05-30
My advice to anyone running the Unity interface is to 
```
apt-get install synaptic
``` 
That will give you the opportunity to add or remove practically anything - for example you could expunge Abiword so you can use the LibreOffice suite that was installed by default.

In my experience I have had endless problems when I tried to use Abiword, and the sort of behavior you describe is quite typical of them.


Edited: I see your thread type listed Lubuntu, but you said you were on Ubuntu 15.04 (Unity).  Abiword is default in Lubuntu, of course, so you have to ADD LibO and remove Abi.  I always do that with Xubuntu as my first configuration.  Don't worry when Synaptic threatens that it will remove Lubuntu - it only means it will remove the metapackage, not the desktop.

---

### Post by kmand on 2015-05-30
I'm not trying to uninstall abiword. I just don't know why I get a compose window when I start the desktop.
It's not a startup application in "Startup Applications Preferences"..

---

### Post by ajgreeny on 2015-05-30
I do not use unity, but is there a method to make the system remember a current session and use it next time, so that if an application is running in minimised state and you inadvertently close down without closing the application it will start in future sessions.

See [http://askubuntu.com/questions/78207/save-unity-desktop-session](http://askubuntu.com/questions/78207/save-unity-desktop-session) for a possible page of info about saving sessions in unity and a downloadable script (scroll to the bottom), though it does sound as if it is not possible to save a session unless you have already used this script.

It may also be worth having a look in /etc/xdg/autostart/ to see if there is a .desktop file for abiword in there, as that will be the reason for abiword starting, though how the .desktop file got there may be a more difficult problem to solve.

However, if such a file is there, open it with **sudo nano /etc/xdg/autostart/abiword.desktop** and try removing the **Exec=abiword %U** line or rename it as a backup to see if it stops abiword starting every boot.

---

### Post by kmand on 2015-05-30
It turns out to be a vivid bug

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1432271](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1432271)

---

