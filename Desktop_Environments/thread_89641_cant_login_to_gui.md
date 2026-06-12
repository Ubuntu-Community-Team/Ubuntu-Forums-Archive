---
title: "cant login to gui"
date: 2005-11-13
forum: Desktop Environments
---

### Post by sunrex on 2005-11-13
im currently stuck in console only mode...it says kdm is running..and gdm is not default..

now i think kdm/kde is the entire problem here since it froze right before i rebooted...can anyone tell me how to make KDM NOT DEFALT, and gdm the defalt....i want to go to gnome for awhile now anyway *yes gnome is installed*

---

### Post by Remmelas on 2005-11-13
this probably isn't the 'best way' to make gdm the default, but, you could ```
sudo rm /etc/rc5.d/*kdm
``` to make gdm the only one that will attempt to launch.

---

### Post by Xian on 2005-11-13
[QUOTE=sunrex]can anyone tell me how to make KDM NOT DEFALT, and gdm the defalt....i want to go to gnome for awhile now anyway *yes gnome is installed*[/QUOTE]
$ sudo dpkg-reconfigure gdm

---

### Post by sunrex on 2005-11-13
i just reinstalled...seems to run faster to..weird..

---

