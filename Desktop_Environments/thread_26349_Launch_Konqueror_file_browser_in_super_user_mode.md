---
title: "Launch Konqueror file browser in super user mode"
date: 2005-04-12
forum: Desktop Environments
---

### Post by NTolerance on 2005-04-12
I've had a heck of a time trying to make a shortcut in KDE that will do this.  I want to click on the shortcut, enter my root password, and then be given the dual-pane file management mode of Konqueror.  I can launch Konqueror in super user mode by using kdesu or setting the user to "root" in the advanced tab of the shortcut, but when I add the "-profile filemanagement" switch to the end of the command, Konqueror won't start.  Conversely I can enable the filemanagement switch but I must remove super user mode in order to do so.   :|

---

### Post by arjaybe on 2005-04-12
Here's what's in the Application/Command slot of my superuser konqueror.

kfmclient openProfile filemanagement

Then in Advanced I have Run as a different user checked.

Sorry I can't be more detailed.  Not in Kubuntu just now.

jim

---

### Post by dermotti on 2005-04-12
This is default in Mepis, ide like to see it in kubuntu

---

### Post by darkaudit on 2005-04-12
IIRC, you need to put the command in quotes, like this:

kdesu "konqueror --profile filemanagement"

---

### Post by NTolerance on 2005-04-12
[QUOTE=arjaybe]Here's what's in the Application/Command slot of my superuser konqueror.

kfmclient openProfile filemanagement

Then in Advanced I have Run as a different user checked.

Sorry I can't be more detailed.  Not in Kubuntu just now.

jim[/QUOTE]

That works great, thanks much.  Got any tricks for running KWrite the same way?  I have a similar setup for my KWrite shortcut except the command is just KWrite without any extra parameters.  I've got the "run as different user" option checked, but this makes KWrite crash on startup after I run it once.  Sometimes it will seem to run the program twice.   :-? 

Edit:  kdesu KWrite has the same crashing problem.  

Edit2:  Now Konqueror is doing the same thing again.  

[QUOTE=dermotti]This is default in Mepis, ide like to see it in kubuntu[/QUOTE]

I just switched from Mepis to Kubuntu.  The Mepis CD is great.  I really like the ability to easily reinstall the X config.  Kubuntu works with my laptop's hardware better though, plus KDE 3.4 looks nicer.

---

### Post by arjaybe on 2005-04-13
[QUOTE=NTolerance]That works great, thanks much.  Got any tricks for running KWrite the same way?  I have a similar setup for my KWrite shortcut except the command is just KWrite without any extra parameters.  I've got the "run as different user" option checked, but this makes KWrite crash on startup after I run it once.  Sometimes it will seem to run the program twice.   :-? 

Edit:  kdesu KWrite has the same crashing problem.  

Edit2:  Now Konqueror is doing the same thing again.  

I just switched from Mepis to Kubuntu.  The Mepis CD is great.  I really like the ability to easily reinstall the X config.  Kubuntu works with my laptop's hardware better though, plus KDE 3.4 looks nicer.[/QUOTE]

For using an editor as root there is the option of using the Run Command - Alt-F2 or on the menu.  kdesu kwrite /etc/fstab, for example.

A good option for a root terminal launcher is: konsole --type su

That puts you straight into the terminal where you enter the password.

---

