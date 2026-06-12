---
title: "lost panel/taskbar"
date: 2007-05-20
forum: Desktop Environments
---

### Post by kadafi69 on 2007-05-20
im pretty new to ubuntu (xfce) i just uninstalled my windows partition so im now on my own with linux. but after my first boot back into ubuntu ive lost my panel/task bar. i did a quick search of the forums and tried a few things but nothing worked.

tried xfce-panel in terminal but it comes up with an error (bash: xfce-panel: command not found)
tried gnome-panel the gnome panel appears but whenever i close the terminal the panel closes too.

im pretty lost at the moment, any one got a clue what else i can do?

---

### Post by ChipG on 2007-05-20
I'm having the same problem, am doing Live CD of Xubuntu on an old HP Pavilion, it comes up fine, but there's no panel/taskbar at the top of the screen! Why?

---

### Post by kadafi69 on 2007-05-20
bump, i need some help for this. still cant seem to find a workable solution

---

### Post by john.nicholls on 2007-05-20
The command is xfce4-panel.

---

### Post by RobbMeex on 2008-05-03
That worked, until I closed the terminal, it closed the panel. Help again!?!

---

### Post by AfterBerner on 2008-05-13
I've had a similar problem with the new 8.04.  I did not have either the top panel or bottom panel in Xfce4 after a bad Firefox crash (don't know why).  

I did however have the floppy drive, trash, home & file system icons on the desktop.  If you have this, go into the File System/usr/bin and find xfce4-panel and simply double click on it.  It will run without the aid of the terminal screen - hence no terminal screen to close and kill the panels.  Make sure to change your logoff settings to save the current settings on exit.  It worked for me and I hope it works for you.

---

