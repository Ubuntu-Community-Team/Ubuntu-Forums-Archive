---
title: "Can't get to login screen after removing KDE"
date: 2009-10-28
forum: Desktop Environments
---

### Post by peterzh on 2009-10-28
I recently decided to try out KDE, but I find gnome suits me better so wanted to remove it. I noticed that doing:

```
sudo apt-get remove kubuntu-desktop
``` 

doesn't actually remove it, so I followed the instructions found  [_**HERE**_]("http://www.psychocats.net/ubuntu/puregnome")

I then restarted my computer, but as soon as it gets to the "Ubuntu" boot screen, the screen goes glitchy, almost as if the screen cable is damaged somehow. It doesn't get to any (visible) login screen. 

So I went into safe mode, dropped down to networked terminal, and tried to undo what had been removed (just replaced "remove" with "install" from before). This didn't help.

I then tried doing
```
sudo dpkg-reconfigure xserver-xorg
```
That didn't help either.

D:

Any assistance would be greatly appreciated!

---

### Post by kellemes on 2009-10-29
Maybe you need to reconfigure the login-manager..
```
dpkg-reconfigure gdm
```
(Choose gdm)

---

