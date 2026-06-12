---
title: "KDE Panel issues"
date: 2009-11-13
forum: Desktop Environments
---

### Post by dazer26 on 2009-11-13
Ok, so I have Kubuntu 9.10 installed on my laptop and my desktop.  

On my desktop I have the main panel at the bottom, and another panel at the top of the screen that I use as a quicklaunch for the programs I use often.  The panel at the bottom spans about 75% of the screen width and I have it centered in the middle.  My problem on my desktop is that everytime I log out and back in the bottom panel is not centered anymore and is at the right of the screen.

On my laptop I have a similar setup, except the quicklaunch panel is on the left side of the screen rather than at the top.  The bottom panel actually stays centered on this computer, the issue is with the panel on the left side of the screen.  Everytime I log out and back in again, all the icons that I added to the panel (and plasmoids) are mixed up (not in the order I left them).

Strangely enough on my desktop the icons on the top panel always stay in the same place....so I have 2 similar but different issues on my 2 computers I guess.  I'm assuming that it has something to do with the settings not being saved properly when I log out.

Any ideas?  Thanks in advance :

edit:  I forgot, on my desktop (not on my laptop tho) I had some permission issues with some files in the /home/user/.kde folder.  Some of the files were owned by root for some reason.  I think I found all the problem files and changed their owner to me.  But this problem still occurs.

---

### Post by lovinglinux on 2009-11-13
The problem with the icon order was happening to me too. The culprit was one of the widgets. Once I removed the "System Monitor" widget from the panel, it stopped messing with the icon order after reboot.

---

