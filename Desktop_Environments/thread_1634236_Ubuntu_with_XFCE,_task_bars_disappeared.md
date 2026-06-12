---
title: "Ubuntu with XFCE, task bars disappeared"
date: 2010-11-30
forum: Desktop Environments
---

### Post by DocMindie on 2010-11-30
For the record, I've NOT installed XUbuntu, it's normal Ubuntu which I've added the XFCE onto.

I installed the upgrades this morning, and had to reboot afterwards (new kernel, I understood) but when I got the box back up and running, the top and bottom bars had disappeared. I've tried to check everything in both the (rightclick on desktop) settings menu and the system menu, but I can't get the bars back. 

I have to rely on CTRR-Fx to switch workspaces and ALT-TAB to switch apps... and it's annoying me. 

Any ideas on how to get them bars back (top bar with the menus and quicklaunchers, bottom bar with the open windows and the workspace-switcher)

---

### Post by 3Miro on 2010-11-30
With right-click on the desktop, you should be able to get to the system menu. Open the task manager and look for "xfce4-panel", if a process exists, kill it. If you cannot go to the menu you can use Alt + F2 to get to the terminal (the command should be just "terminal"). From there you can search for running processes:
```
 ps -e | grep xfce 
```
and kill the panel with the kill command (give it the process ID).

If there is no xfce4-panel running, hit Alt + F2 and type:
```
 xfce4-panel 
```

---

### Post by DocMindie on 2010-11-30
Thanks alot, 3Miro, for some reason the panels wasn't started on reboot.

---

