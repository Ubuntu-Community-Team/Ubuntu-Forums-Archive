---
title: "Rebuild Desktop Search?"
date: 2020-05-31
forum: Desktop Environments
---

### Post by deltoni on 2020-05-31
Dear all,

recently, I uninstalled the evolution database management system and reinstalled it. (The purpose was to get rid of date notifications from the calendar, but that didn't work out either). I use Ubuntu 20.04 but the problem stems from a previous installation (19).

Now the (standard unity) desktop search does not work anymore. I can not search (upper left button on the desktop) for programs installed. The search query will open but never yield any results.

Is there a way to rebuild that database or to reinstall packages? Reinstalling the desktop or unity did not fix the problem so far.

Thanks in advance,

regards,

 Josh

---

### Post by mc4man on 2020-05-31
Sorta sounds like the application lens ins't installed?
Try this, see if anything other than the metapackage is to be installed
```
sudo apt install ubuntu-unity-desktop
```
If the lens or other related is mentioned you can answer Y or go N &  install specifically

---

### Post by deltoni on 2020-05-31
great hint, that cured the desktop search. Thanks!

---

### Post by ajgreeny on 2020-05-31
Great news! 

Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

