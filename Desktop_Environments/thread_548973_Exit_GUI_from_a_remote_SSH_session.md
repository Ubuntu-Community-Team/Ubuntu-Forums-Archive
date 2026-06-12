---
title: "Exit GUI from a remote SSH session"
date: 2007-09-11
forum: Desktop Environments
---

### Post by KyferEz on 2007-09-11
I have a Ubuntu machine that I would like to remotely tell the GUI to exit. I don't want to kill it! I want to properly instruct it to exit the GUI. Doing a reboot is not viable as the GUI is set to auto start on reboot and I don't want that to change.

Why do I need to do this? Because I'm not at the PC and won't be for weeks. I'm remotely logged in via SSH and want to free up the RAM that the GUI is using.

What would that command line instruction be? I did search these forums and google, but all I come up with is how to start the gui, no command line commands to exit it :confused:

Thanks!
KyferEz

---

### Post by ruibernardo on 2007-09-12
If you have Gnome installed, you can stop it with:

```
 sudo /etc/init.d/gdm stop
```

If it is KDE (Kubuntu) it is:

```
 sudo /etc/init.d/kdm stop
```

This will stop the GUI, closing Gnome/KDE normally. On the computer itself, you wont have any login screen, just the tty consoles. The next time you boot the computer, Gnome/KDE will start as expected. 

If in the meanwhile, you need to start Gnome/KDE again, just "start" them again.

---

### Post by KyferEz on 2007-09-12
Thank You Very Much!

---

