---
title: "howto stop gnome"
date: 2005-12-27
forum: Desktop Environments
---

### Post by fugedi_zsolt on 2005-12-27
Hi,
I want to manually start and stop gnome (GUI).
I want to login in a command-line shell without GUI and I want to start GUI.
Please help, what to do.
Thanks a lot

Fuge

---

### Post by Lord Illidan on 2005-12-27
If you want to start from a command line, completely bypassing the gui, choose the failsafe option at boot.

Otherwise, type this in a terminal

```
sudo /etc/init.d/gdm stop
```

then when you are ready

```
sudo /etc/init.d/gdm start
```

---

### Post by schilcha on 2005-12-27
You can also try 
```
 sudo update-rc.d -f gdm remove
```
to prevent gdm from being launched during startup.

---

### Post by fugedi_zsolt on 2005-12-27
Thanks a lot! You are really fast, and helpful.
Fuge

---

