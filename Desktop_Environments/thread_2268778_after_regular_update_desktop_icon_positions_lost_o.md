---
title: "after regular update desktop icon positions lost on each boot (ubuntu studio or xubun"
date: 2015-03-11
forum: Desktop Environments
---

### Post by a-you on 2015-03-11
This is a minor issue, but a drag: every time I boot now about half of the icons on the desktop lose their position, ending up in a line down the left side of the screen. None of the icons are missing though. 
I have tried clearing the saved sessions and disabling the saving of  sessions, both just by using the GUI Sessions Manager->Session and  Startup tool.

This is ubuntu studio 14.4 trusty 64 bit; maybe some users of xubuntu have the same issue? Or I wonder if anybody is experiencing this (searches don't seem to show anybody else having this)??

Thanks in advance for any thoughts.

---

### Post by ajgreeny on 2015-03-11
Yes, it's a known problem in xfce; I used to suffer from it in both xubuntu 12.04 and 14.04 but now have stopped it happening by making the config files that relate to the icon placement immutable.  First remove all the **icons.screens*** files in .config/xfce4/desktop except for the most recent, as there may be several, and it is easier if you have only one icons file in that folder

Now put all the icons where you want them then run command ```
sudo chattr +i .config/xfce4/desktop/icons*
``` This will mean that the config file can not be changed at all, even by root, nor can it be deleted, but it also means that the icons will not move in normal situations, and if they should you can just click on the desktop and hit F5 to refresh the desktop; this will put the icons back to where they should be.

If you need to move icons or add new ones you will need to remove the immutable flag with ```
sudo chattr -i .config/xfce4/desktop/icons*
```then add or move icons then run the first command again.

---

### Post by a-you on 2015-03-11
Wow that's a pretty permanent solution, but thanks. At the moment I have instead just gotten rid of most of the icons that I had on the desktop. But if it gets to be too irritatiing I'll try your method.

---

### Post by ajgreeny on 2015-03-11
It's only as permanent as the file is immutable, and that takes only a few seconds to change, particularly if you alias the commands to a command such as **icons****+  **and **icons-**.

I don't use my desktop as a place to store files for more than a few minutes, so I don't have changes to the icons used.  Actually I don't use icons on the desktop generally now but a panel on the left hand edge (a bit like the unity launchbar) which is stuffed full of launchers and autohides.

---

