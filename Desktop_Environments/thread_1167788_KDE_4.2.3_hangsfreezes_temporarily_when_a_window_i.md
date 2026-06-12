---
title: "KDE 4.2.3 hangs/freezes temporarily when a window is closed"
date: 2009-05-23
forum: Desktop Environments
---

### Post by gnufied on 2009-05-23
Hi folks,

For any KDE 4.2.x release I have a weird problem that whenever I close a window (which has some amount of artifacts such as Firefox with few tabs, Emacs with few files open or konsole with tabs) it freezes KDE temporarily (for about 10-15 seconds).

I have NVIDIA 8400M GS graphics card on Dell Inspiron 1520 and I am using latest updated drivers (180.51).

I have tried creating a bug report on KDE bug tracker ([https://bugs.kde.org/show_bug.cgi?id=185671](https://bugs.kde.org/show_bug.cgi?id=185671)) and tried to file a report with NVIDIA folks ([http://www.nvnews.net/vbulletin/showthread.php?t=132220](http://www.nvnews.net/vbulletin/showthread.php?t=132220)) but all is vain.

Does anyone else has this issue, did you found any fix?

---

### Post by krazyd on 2009-05-24
I don't have the issue on my geforce 6400 running the default jaunty nvidia drivers. 

As Martin says in the KDE bug report, it's extremely hard or impossible for KDE to track down the cause of bugs like this if closed source drivers are involved (like nvidia's). This is because there is no way of understanding what the driver is doing and how it is interacting with KDE without seeing the source code of both.

You can either keep bugging nvidia and hope they fix the bug, or try a different version of the driver and hope it doesn't have the bug.

Such are the joys of proprietary graphics drivers...

---

