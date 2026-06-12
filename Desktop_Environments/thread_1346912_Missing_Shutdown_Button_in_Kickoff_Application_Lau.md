---
title: "Missing Shutdown Button in Kickoff Application Launcher"
date: 2009-12-05
forum: Desktop Environments
---

### Post by zggame on 2009-12-05
I used to use gnome in 9.0.4 and I update to 9.10.  I have a 1366x768 screen and I would like to put the taskbar/launcher on the left.  Gnome has that option, but it keeps freezing on me and really not cut for it.   I have added KDE desktop afterward and it works much better.  One weird thing is that I cannot find a shutdown button.  I have logoff/lock/switch user/sleep/hibernate in the leave section.  But no shutoff.  I do see one in the lancelot launcher.  I can use the "sudo shutdown -P now" though, but it is a bit annoying.

---

### Post by bailout on 2009-12-05
If you have installed kubuntu over ubuntu  then you are probably logging in via gdm? It is a while since I have had both installed but I seem to remember that shutdown only appeared in the desktop related to your logon manager. Try searching for installing and swapping to kdm instead of gdm.

---

### Post by Zorael on 2009-12-08
Yes, neither gdm/KDE nor kdm/GNOME combinations seem to work to satisfaction. The upstream KDE bug report is [here](https://bugs.kde.org/show_bug.cgi?id=214654), if you want to comment on it (and vote for it to get attention).

---

### Post by engelp on 2010-02-25
I followed the bug link but even saying it is resolved i couldnt find a workaround any sugestions? 
Should when installing kde-desktop prefer kdm if it is going to be my default desktop?

Thanks

---

### Post by WinterMadness on 2010-02-25
```
    sudo dpkg-reconfigure gdm

```

do that, pick KDM.

I think that might work.

---

### Post by vys on 2010-12-01
I had the same problem and ^ that was the solution.

---

