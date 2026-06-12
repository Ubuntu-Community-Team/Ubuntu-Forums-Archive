---
title: "Native port of Cave Story"
date: 2007-09-20
forum: Gaming &amp; Leisure
---

### Post by DoktorSeven on 2007-09-20
[doukutsu: Linux port](http://community.livejournal.com/doukutsu/101690.html)

Link was posted on Linux Game Tome today.  Download, extract, and run **doukutsu**.  The DoConfig.exe to configure it is still a Windows binary, though, but Wine can run it fine.

---

### Post by rybu on 2007-09-21
If you have to run wine, it's not a native port.  It would be native Windows app that is wine compatible.

---

### Post by DoktorSeven on 2007-09-21
You did not understand.

Only the configuration application is a Windows binary.  The game itself is a Linux native binary. 

```
$ file doukutsu 
doukutsu: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), not stripped

```

---

### Post by TheBlueCow on 2007-09-25
Sweet! For some reason though, whenever I start it from a menu (using Fluxbox, not sure if that matters) it quits automatically. I can start it by double clicking it in Nautilus or from a terminal, but not otherwise. Any ideas?

EDIT: Fixed! You have to run it from it's directory or else it can't find the game files. cd ~/doukutsu && ~/doukutsu/doukutsu

---

### Post by n2j3 on 2007-11-27
[http://ubuntuforums.org/showthread.php?p=3847287](http://ubuntuforums.org/showthread.php?p=3847287) < since the livejournal download  url is down.

---

