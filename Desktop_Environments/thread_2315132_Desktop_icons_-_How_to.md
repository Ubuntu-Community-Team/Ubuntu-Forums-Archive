---
title: "Desktop icons - How to?"
date: 2016-02-26
forum: Desktop Environments
---

### Post by bigred2012 on 2016-02-26
Hi,

I've recently installed Kubuntu 15.10 and really like KDE in general.  However I am stumped as to how I can create a desktop icon (Windows style).  Can anyone help me out with this?  Thanks.

:confused:

---

### Post by claracc on 2016-02-28
This is, [https://forum.kde.org/viewtopic.php?f=67&t=98673](https://forum.kde.org/viewtopic.php?f=67&t=98673) what I have found about the question.

Perhaps you will obtain better responser in kde fora.

---

### Post by montag dp on 2016-02-28
Two things. First, you need a .desktop file, which is the actual launcher ("shortcut " in Windows). If there is an entry for your program in the applications menu, then the .desktop file already exists, either in /usr/share/applications or ~/.local/share/applications. If not, you can use one of the launchers there as a guide to create your own.

Next, put this .desktop file in your Desktop directory. If it doesn't appear, it's because your desktop is not set to be a Folder View. Right click on the desktop, select Desktop Settings, and in the first drop-down, change Desktop Type to Folder View. Then your launcher should show up on the desktop.

All that being said, having launchers scattered all over the desktop is not a good practice, IMO, unless you want your desktop to look like a typical cluttered Windows mess. (I do recognize that you can put launchers on the desktop and not have it cluttered, but most Windows users I've seen don't do that.) You should instead add them to the panel or favorites menu, both of which you can do by navigating to or searching for the program in the applications menu, right clicking, and choosing the appropriate option.

---

### Post by bigred2012 on 2016-03-04
Thank you for your help!

:D

---

