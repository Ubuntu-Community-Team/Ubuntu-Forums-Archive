---
title: "Ubuntu 6.06 login problem"
date: 2008-07-28
forum: Desktop Environments
---

### Post by picks on 2008-07-28
I've been using the Ubuntu server (with Gnome[ubuntu-desktop] installed) for a few days in a Paralells virtual machine, running on OS X 10.5. I've installed Nagios (SNMP server monitoring software), and it's been working perfectly well.

But as of a few hours ago, I can't get past the login screen. I type in my username and password, and the screen goes into a shell login screen. Seemingly randomly, the login GUI decides to start up again while I'm using the shell session. I can login and do everything in the shell, but I need my GUI back. Without logging in, the server runs perfectly fine (I can access the external IP and apache+nagios works the same).#-o

Thanks!

---

### Post by p_quarles on 2008-07-28
Typically, a Linux GUI will start in one of two ways: 1) via a login manager, such as GDM; 2) via a startx script. You should be able to cause the first method to begin by running:
```
sudo /etc/init.d/gdm start
```
The second method should work by running:
```
startx gnome-session
```
Try whichever you prefer. The command is likely to fail, but should produce interesting output in doing so. That will help get to the bottom of things.

---

### Post by picks on 2008-07-28
> **p_quarles said:**
> Typically, a Linux GUI will start in one of two ways: 1) via a login manager, such as GDM; 2) via a startx script. You should be able to cause the first method to begin by running:
```
sudo /etc/init.d/gdm start
```
The second method should work by running:
```
startx gnome-session
```
Try whichever you prefer. The command is likely to fail, but should produce interesting output in doing so. That will help get to the bottom of things.

gdm start came out [ ok ], but nothing happened afterwards (except in recovery mode, it went into the login screen). Startx, however, came out with
```
xauth: error in locking authority file /home/sysadmin/.Xauthority

```

---

