---
title: "KDE splash screen issue"
date: 2005-08-17
forum: Desktop Environments
---

### Post by stevea1210 on 2005-08-17
I just switched distros from Mandriva to Kubuntu.  I had created several splash screens for my mandriva install that worked fine under KDE 3.2 and 3.3.  I moved them to my Kubuntu install, and have had some issues.

They added fine, and tested fine.  When I selected one of them, logged/off/on, I got an error of /home/username/.kde/apps/share/cpmfig/ksplashrc not being writable, configuration will not be saved.    I checked and I didn’t have write access to the file.  I changed the permissions, and owner of the file so I was the owner (was root), and everyone had read/write access.  

Log off/on again.  That error is now gone, however, my splash screen isn’t the one I selected, it is now the default KDE one.  Not the default Kubuntu one, but the default KDE one.  I checked ksplashrc, and it lists the splash screen I selected in that file.  For some reason, it is ignoring that setting.  Basically, I fixed one problem but caused another.

Please forgive me if the path or filename is off by a little.  I am posting from work in XP, not at home in Kubuntu.

Any help would be appreciated.

---

