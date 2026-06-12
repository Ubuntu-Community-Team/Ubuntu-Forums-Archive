---
title: "No panels after deleting config and re-installing desktop"
date: 2009-12-17
forum: Desktop Environments
---

### Post by adelphos on 2009-12-17
I had to use a hard (BIOS) shutdown while using Ubuntu. Upon start-up it ran the disk-check and everything seemed fine. However, when I logged in there were no panels and alt-f2 would not bring up a command window. I could, however, access the right click menu and the "appearance" window and so forth. So, it seemed that gnome-panel wasn't working at all. I tried several things to get it to appear, but nothing worked.

So, I installed kubuntu-desktop and uninstalled as many of the gnome packages as I could, definitely gnome-panel and its data and nautilus and many others and the base gnome libraries. Also ran 
```
[INDENT]**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**
[/INDENT]
```
But upon reinstalling ubuntu-desktop, the panels were still not there. Any help or ideas?

---

### Post by Ylon on 2009-12-17
Have you try to run gnome-panel in terminal and see if there are any error logs?
[alt]+[f2] > xterm > **gnome-panel**

---

### Post by adelphos on 2009-12-17
Thank you for the reply. I can't use alt-f4 without gnome-panel, but using the right-click menu to launch a terminal and running "gnome-panel" does bring up the panels and everything. This will work as a temporary solution. However, when a new GNOME session is begun, gnome-panel doesn't launch automatically. Also, I have to keep the terminal open in which I ran the gnome-panel command (adding the command as a startup launcher doesn't work).

Where would I look to find the error log for something like this? Any idea how to get gnome-panel to execute on startup?

---

### Post by Ylon on 2009-12-18
In [this post](http://ubuntuforums.org/showpost.php?p=8495431&postcount=14) ([full thread](http://ubuntuforums.org/showthread.php?t=1293789) some one seems to have solved this problem (which looks like yours).

---

