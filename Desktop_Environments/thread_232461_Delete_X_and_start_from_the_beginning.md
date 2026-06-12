---
title: "Delete X and start from the beginning"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Can0n on 2006-08-08
I wanna start from the beginning with X and everything that comes with that, all the WMs and the configs and everything. How do I do that ?
I just wanna have KDE installed as a WM and nothing else, just like Kubuntu but I dont wanna install Kubuntu all over again cause I wanna keep my /home folder.

Will bli glad for every helpfull answer I get =)

---

### Post by Ocxic on 2006-08-08
well from a console (alt+ctrl+f2) type "sudo apt-get remove ubuntu-desktop" (or kubuntu-desktop wichever you have installed, also uninstall any other WM's you've installed)
this will basically convert you computer into a server, then type "sudo apt-get install kubuntu-desktop". this will install kde and such.

WARNING: this will remove alot of other programs like e-mail, firefox, and such, wich should be safe on your home folder, but make buckups just to be safe.

if you home directory isn't touched, the e-mail and app settings will remain the same, along with your desktop layout.

if need be run "sudo dpkg-reconfigure xserver-xorg" to reconfigure the xserver.

---

### Post by someguyouknow on 2006-08-08
I think you have to go and uninstall the other WMs but to reset X use this.....
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Can0n on 2006-08-08
OKey, thank you for the answers =)
Im gonno try that the first thing in the morning, going to bed now.

---

