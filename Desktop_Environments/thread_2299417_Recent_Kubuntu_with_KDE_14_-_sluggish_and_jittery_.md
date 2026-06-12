---
title: "Recent Kubuntu with KDE 14 - sluggish and jittery graphics"
date: 2015-10-18
forum: Desktop Environments
---

### Post by richlion2 on 2015-10-18
Hi, 

I just wanted to let you know that the recent new installation of Kubuntu with KDE 4.14.6 seems to have a problem with graphics cards. I have both ATI and Nvidia cards. All are showing similar problems I thought were down to KDE doing something wrong, here's my post:
[https://forum.kde.org/viewtopic.php?f=225&t=128847](https://forum.kde.org/viewtopic.php?f=225&t=128847)

I think I found the solution on this link:
[https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

I ran the install command for my ATI card:
[COLOR=#111111][FONT=Consolas]sudo apt-get install fglrx

[/FONT][/COLOR]After the reboot the graphics seem to be performing well now.

I think I'll mark this thread as resolved, but if anyone has other ideas, feel free to say so.

Regards, 
Richlion

---

