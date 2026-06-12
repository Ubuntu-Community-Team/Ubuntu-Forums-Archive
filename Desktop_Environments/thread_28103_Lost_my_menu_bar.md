---
title: "Lost my menu bar"
date: 2005-04-18
forum: Desktop Environments
---

### Post by Tanizaki on 2005-04-18
I'm a linux newb and have just installed Hoary on a box to use as a file server. After installing Samba and rebooting, the bar at the top of the desktop that has the drop-down menus has vanished. How can I get it back? Please advise so I can finish my Samba setup!

TIA!

---

### Post by bored2k on 2005-04-18
[QUOTE=Tanizaki]I'm a linux newb and have just installed Hoary on a box to use as a file server. After installing Samba and rebooting, the bar at the top of the desktop that has the drop-down menus has vanished. How can I get it back? Please advise so I can finish my Samba setup!

TIA![/QUOTE]
 Try killall gnome-panel. It should restart the panel.

---

### Post by Tanizaki on 2005-04-18
[QUOTE=bored2k]Try killall gnome-panel. It should restart the panel.[/QUOTE]
That worked. Thanks!

---

### Post by BiynaYahu on 2008-06-06
I have also lost my menu bar.  The task bar as well.  It happened after I installed the kernel source for VirtualBox-OSE.  I haven't been able to try the first advice because I can't figure out how to start terminal.  I can't create a launcher on the desktop I've tried.  It simply won't let me create launcher's at all.  If someone could help me I'd appreciate it, and Yah guide you.

Peace,
Mike Browell

Solved By this Post: [http://ubuntuforums.org/showthread.php?t=812972&highlight=lost+gnome-panel]("http://ubuntuforums.org/showthread.php?t=812972&highlight=lost+gnome-panel")  Although I did "emerge gnome-core" so as not to install evolution mail, and only the necessary components of gnome.

---

