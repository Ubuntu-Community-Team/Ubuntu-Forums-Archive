---
title: "KDM to GDM"
date: 2005-12-27
forum: General Help
---

### Post by kenweill on 2005-12-27
I have recently installed kubuntu-desktop and replaced GDM to KDM.

How can I return to GDM from KDM?
I just want to display the Ubuntu login instead of Kubuntu login screen.

---

### Post by mfarquhar on 2005-12-27
DID you delete GNOME (ubuntu-desktop)
do you want to remove KDE

this will remove KDE (KDM)
```
apt-get uninstall kubuntu-desktop
```


this will install GNOME (GDM)
```
apt-get install ubuntu-desktop
```


correct me if i'm wrong people

---

### Post by anil_robo on 2005-12-27
I was using GNOME and then decided to install KDE too. So I installed KDM as a part of a large number of packages. There was a prompt on the screen like "which one do you want to use to login" and I chose KDE.

After trying KDE for some time, I decided to go back to GNOME. So I removed every package in KDE, and when I was removing KDM, the same screen appeared again and asked me "which one do you want to use to login" and I selected GNOME.

Rebooted to check, and all was back to normal.

Additionally, I guess he has to install GDM before removing KDM. Or else, the system might become unstable - he shall land up with a command-line prompt to say the least!

---

### Post by kenweill on 2005-12-27
No. I did not uninstall GNOME.
ubuntu-desktop and kubuntu-desktop are both installed.
I just want to have the ubuntu login screen back. After I've installed kubuntu-desktop and installed kdm, i got the kubuntu login screen.

My problem is going back to the ubuntu login screen.

---

### Post by cjazz on 2005-12-27
Entering the command

dpkg-reconfigure gdm

(or "dpkg-reconfigure kdm," for that matter)

should allow you to choose which display manager to use.

---

### Post by mitchellthegreat on 2007-12-12
I have ubuntu 7.10 I had kdm as defualt. using other sources, i got it back to gdm. only here's the problem, the booting bar (or loading bar that u get during boot) still says kubuntu. i tried doing the sudo command to get rid of it, but it says invalid operation: uninstall

i've done autoremove, but it says that its doing everything, but i get nothing.


help!

---

### Post by p_quarles on 2007-12-12
> **mitchellthegreat said:**
> I have ubuntu 7.10 I had kdm as defualt. using other sources, i got it back to gdm. only here's the problem, the booting bar (or loading bar that u get during boot) still says kubuntu. i tried doing the sudo command to get rid of it, but it says invalid operation: uninstall

i've done autoremove, but it says that its doing everything, but i get nothing.


help!
That has nothing to do with KDM, it's just the Kubuntu usplash screen. Here's the community documentation on switching between usplash artwork packages (as well as using custom art):
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

---

