---
title: "icons and gnome"
date: 2005-04-18
forum: Desktop Environments
---

### Post by egreggio dottore on 2005-04-18
I have just installed grubconf, a graphical tool for grub and the program puts an icon on system programs. I clic over and the answer is "no, you need to be root" and stops it. If I use terminal, sudo and password and type grubconf, it open the program well. Two questions: How may I erase or eliminate the icon the installer program put on my menu-gnome? Whta are the instructions I need to write and wher to open the program by clic over the icon?
Thanks

---

### Post by Bob D. on 2005-04-18
To remove the menu entry, you need to find and remove the grubconf,desktop file. This needs to done from the terminal with root privileges. Be careful, you can delete things you really do not want to (read, you can ruin your installation).

EDIT: *the section that was here was dead wrong and I don't know the correct way, so I deleted what I wrote. *

I have grubconf installed as well and honestly didn't know it even installed an icon into the menu. I'd recommend either just ignoring it and running from the terminal or deleting the .desktop file.

Bob

---

### Post by Bob D. on 2005-04-18
I have a solution!

1. In a terminal, type 'sudo gedit /usr/share/gnome/apps/Applications/grubconf.desktop

2. In the file that opens, edit the 'Exec=' line to 'Exec=gksudo /usr/sbin/grubconf'

3. Save the edited file and exit.

Now when you launch grubconf from the user menu you will be asked for your password, just like when you run Synaptic.

Bob

---

