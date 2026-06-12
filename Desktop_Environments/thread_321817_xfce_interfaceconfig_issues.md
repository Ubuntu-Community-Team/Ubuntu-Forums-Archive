---
title: "xfce interface/config issues"
date: 2006-12-19
forum: Desktop Environments
---

### Post by blue_shift on 2006-12-19
I'm running Kubuntu Dapper and KDE 3.5.5. I recently installed the package xfce4-desktop and some related packages. When I start an xfce session, I encounter some problems. 

Firstly, there is no right-click menu on the desktop. Secondly, the majority of the config menus don't respond when run from the Xfce menu on the taskbar. Preferred applications, menu editor  and autostart menus do work, but almost all others do not. 

If I run *xfce-settings-show* from the CLI I get this, but no settings menu:
```
alex@alex-desktop:~/Desktop$ xfce-setting-show
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
alex@alex-desktop:~/Desktop$ X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

I don't know how to fix these problems, nor use xfce without access to these config menus. Any suggestions greatly appreciated. 

Most apps seem to run fine on xfce by the way; I'm running Firefox 2.0, adept and konsole from it now without problems.

Thanks.

---

### Post by kerry_s on 2006-12-19
When you say you installed "xfce4-desktop" did you install xfce4 or xubuntu-desktop? 

xfce4 is just the core of xfce4 desktop, it's not the entire desktop, there are still more parts.

---

### Post by zubrug on 2006-12-19
sudo aptitude install xubuntu-desktop

---

### Post by blue_shift on 2006-12-20
Thanks, issue resolved.

---

