---
title: "Install ubuntu desktop how to start Unity?"
date: 2016-06-01
forum: Desktop Environments
---

### Post by LMH1 on 2016-06-01
Hi i tryed to install from kubuntu:

```
sudo apt-get install ubuntu-desktop 
```

Tryed to reinstall ubuntu-desktop
```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo shutdown -r now

rm -rf ~/.config
***rm -rf .compiz-1***
```

But still i only get a steam icon, nothing else.
do i need to make boot script unity or unity-2d-shell?

Or is that a bug in kubuntu?

KDE\XFCE 4 works nice.

---

### Post by ZoiaGuyver on 2016-06-01
You need to apt install ubuntu-session aswell. 

If you add that package you should get a selection dropdown in lightdm/KDM (normally a little cog next to your name) that will allow you to start a Unity session.

---

### Post by LMH1 on 2016-06-01
So i did not need to:
> sudo apt-get install gnome-session
sudo apt-get install lightdm
sudo apt-get install unity-greeter
sudo dpkg-reconfigure lightdm

This is only if you command did not works?

Do you also know 
Sudo apt-get install xfce-goodies
Is it a part of apt-get install xfce4-desktop?
Or is this package outdated so not longer in use?

---

### Post by ajgreeny on 2016-06-01
>     Sudo apt-get install xfce-goodies
    Is it a part of apt-get install xfce4-desktop?
    Or is this package outdated so not longer in use? 
That package contains a lot of extras to the xfce4-desktop so if you do not already use either xubuntu-desktop or xfce4-desktop there is little point installing it.  If you do decide to install it you will end up bringing in a large number of other xfce4 packages and will probably end up with a very confusing menu system with a lot of alternative text-editors, file-managers, etc etc available to you.

---

### Post by vasa1 on 2016-06-01
So you have Kubuntu, Ubuntu (Unity) and Xfce all at the same time? I've read of many instances where Kubuntu and Unity seem to "clash". Same with Unity and GNOME. Re. Xfce, some people get all excited about how the notifications appear "different".

---

### Post by CantankRus on 2016-06-01
The unity plugin for compiz may not be enabled.
Reset compiz to default via terminal...
```
dconf reset -f /org/compiz/
```
Logout....
```
kill -9 -1
```


You can run the command from your xfce session if you can't access a terminal in the Ubuntu session.

---

### Post by LMH1 on 2016-06-01
I tested:
sudi apt get install ubuntu-session
sudo apt-get install unity-greeter

But still same issue, only steam icon, without unity.
I want to test many desktop, i know this works better before?

---

