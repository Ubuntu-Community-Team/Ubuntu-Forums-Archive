---
title: "administative access from nautilus"
date: 2009-01-27
forum: Desktop Environments
---

### Post by tlknv on 2009-01-27
I'm a newbie to Ubuntu and Gnome. Is there anyway to do simple operation from nautilus with administrative rights ? Every time when I need to edit some file from /etc ( for example /etc/X11/xorg.conf ) or copy files from/to another partition on HDD I run terminal and execute gedit /etc/X11/xorg.cong, sudo nautilus, etc.
It doesn't seem intuitively.
1) I couldn't even know the names of the applications I has to run ( sudo, gedit, nautilus, etc. ).
2) I could try to find the names of the running application in some task manager however I didn't find any besides the applet for the panel.
3) I would expect something like "Run as" in the local/context menu for the current/selected item.

---

### Post by oldos2er on 2009-01-27
Install the package nautilus-gksu, then restart X. This will give you a menu entry 'Open as Administrator' when you right-click on a file.

 Btw, when calling graphical programs e.g. Nautilus or gedit, use 'gksu' in place of 'sudo.'

---

### Post by tlknv on 2009-01-27
Thanks a lot !
Very bad that nautilus-gksu is not installed initially.

---

### Post by oldos2er on 2009-01-27
> **tlknv said:**
> Thanks a lot !
Very bad that nautilus-gksu is not installed initially.

 There are many useful packages that aren't installed initially.

---

### Post by tlknv on 2009-01-27
I think that packages like that supposed to be essential because most people have to access other partitions, edit files in /etc, etc.
I thought it's a purpose of Ubuntu to make linux user friendly and allow newcomers to really work with linux. I think that's why Ubuntu has lots of heavy but user friendly applications.

---

