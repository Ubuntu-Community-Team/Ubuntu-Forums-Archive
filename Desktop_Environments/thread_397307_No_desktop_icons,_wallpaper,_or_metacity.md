---
title: "No desktop icons, wallpaper, or metacity"
date: 2007-03-30
forum: Desktop Environments
---

### Post by ikes on 2007-03-30
I'm running Edgy and I have 3 possibly related issues.  

Problem #1: When I first log into Ubuntu, metacity does not start.  I need to start it from a shell.  Then it works fine for the rest of the session.  So metacity is there.  I found a post to check /etc/alteratives/x-window-manager and it looks correct:

deichenwald@framingham:~$ ls -l /etc/alternatives/x-window-manager
lrwxrwxrwx 1 root root 17 2007-03-30 09:47 /etc/alternatives/x-window-manager -> /usr/bin/metacity
deichenwald@framingham:~$ which metacity
/usr/bin/metacity
deichenwald@framingham:~$ ls -l /usr/bin/metacity
-rwxr-xr-x 1 root root 464204 2006-10-05 09:37 /usr/bin/metacity

Problem #2: I have no icons on my desktop.  I found a post to fire up gconf-editor, do a "find" for nautilus, and under /apps/nautilus/desktop, check all of the icons boxes.  I did this, logged out and logged back in and I still dont see anything.  There is plenty of stuff on my Desktop if I navigate to in a shell

Problem #3: I don't have any wallpaper when I log in.  As soon as I open System->Desktop Background, my wall paper appears.  I don't even have to select it.

Any help on these issues would be greatly appreciated.

Thanks,
Dan

---

### Post by ardchoille42 on 2007-03-30
> **ikes said:**
> I'm running Edgy and I have 3 possibly related issues.  

Problem #1: When I first log into Ubuntu, metacity does not start.  I need to start it from a shell.  Then it works fine for the rest of the session.  So metacity is there.  I found a post to check /etc/alteratives/x-window-manager and it looks correct:

deichenwald@framingham:~$ ls -l /etc/alternatives/x-window-manager
lrwxrwxrwx 1 root root 17 2007-03-30 09:47 /etc/alternatives/x-window-manager -> /usr/bin/metacity
deichenwald@framingham:~$ which metacity
/usr/bin/metacity
deichenwald@framingham:~$ ls -l /usr/bin/metacity
-rwxr-xr-x 1 root root 464204 2006-10-05 09:37 /usr/bin/metacity

Problem #2: I have no icons on my desktop.  I found a post to fire up gconf-editor, do a "find" for nautilus, and under /apps/nautilus/desktop, check all of the icons boxes.  I did this, logged out and logged back in and I still dont see anything.  There is plenty of stuff on my Desktop if I navigate to in a shell

Problem #3: I don't have any wallpaper when I log in.  As soon as I open System->Desktop Background, my wall paper appears.  I don't even have to select it.

Any help on these issues would be greatly appreciated.

Thanks,
Dan

The desktop icons and wallpaper, along with the desktop right click menu, are all managed by nautilus. It sounds as if nautilus isn't starting up. Since you are having problems with Metacity, and nautilus, I am thinking that your session got borked somehow. I don't know how to fix it, I just wanted to let you know about nautilus' management of the desktop as that may help you troubleshoot the problem.

---

