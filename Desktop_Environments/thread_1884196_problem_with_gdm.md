---
title: "problem with gdm"
date: 2011-11-20
forum: Desktop Environments
---

### Post by leeper69 on 2011-11-20
Hi I have installed Ubuntu 11.10 on my computer and am using gdm as my desktop loader. everything was working fine and I had Gnome classic set up as I like it when gdm decided to crash now it is all not accessible all I get is the start up screen for Ubuntu then I am kicked out to the shell and froze up, all I can do is restart the system.Fortunately I have Kubuntu 11.10 loaded with multiple desktops and kdm as there desktop loader. I have run e2fsck on the drive with Ubuuntu 11.10 but it is still hanging in the same spot. I had problems with gdm on the Kubuntu install and chose kdm for that drive the second time around. can anyone tell me how to repair gdm? I really don't want to go through the process of reloading Ubuntu for the second time. has anyone had problems with gdm?

---

### Post by typhoon_tip on 2011-11-20
Have you been trying to tweak some Compiz settings ?

---

### Post by leeper69 on 2011-11-21
no I dont use compubiz.

---

### Post by sammiev on 2011-11-21
If you are making it to the login screen select gnome3 or unity and see what happens. :)

---

### Post by jimmydean886-2 on 2011-11-21
If you are getting a command line in the Ubuntu install, try typing in
```
~$ sudo apt-get install kdm
-or-
~$ sudo dpkg-reconfigure lightdm
```

Although it won't let you use GDM, you'll at least be able to use your desktop.

---

### Post by leeper69 on 2011-11-23
Hi and thanks for answering my post!
I wasn't getting a prompt after the Ubuntu boot screen just a message that pulse audio was shutting down. no mouse or keyboard input. I finally just reloaded Ubuntu and tried to get lightdm to load but was only kicked into the Ubuntu login page, so I am using KDM as my desktop loader. so far it is working fine. 
a special thanks to jimmydean886-2 for the terminal commands!

---

### Post by sammiev on 2011-11-23
If you want to play a little more this might help you with different settings. [Here]("https://wiki.ubuntu.com/LightDM") and [Here]("http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html"). :)

---

