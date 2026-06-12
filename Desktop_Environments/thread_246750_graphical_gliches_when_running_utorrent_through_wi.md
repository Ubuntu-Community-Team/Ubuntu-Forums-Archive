---
title: "graphical gliches when running utorrent through wine"
date: 2006-08-29
forum: Desktop Environments
---

### Post by 13east on 2006-08-29
just started running utorrent and see that there are a lot of graphical gliches witht the program running in wine.  the main one being that after i minimize the program to taskbar, i can't maximize it; all i get is the windows edge with nothing inside it and have to double click the system tray icon to get it to work again.  i'm assuming the next prblm also has to do with this: i can't get utorrent to close to the tray; whenever i click the close button it minimizes instead of going to the system tray.  these aren't major prblms but are kinda annoying. so thanks in advance.

---

### Post by orb9220 on 2006-08-29
Run winecfg select app and on graphics tab i believe thier is a check on double-buffering uncheck it and apply.

Don't know if it will work on utorrent but try it and report resusts.

---

### Post by 13east on 2006-08-29
> **orb9220 said:**
> Run winecfg select app and on graphics tab i believe thier is a check on double-buffering uncheck it and apply.

Don't know if it will work on utorrent but try it and report resusts.

no progress
thx for the help though

---

### Post by Cable on 2006-08-29
I believe the problem you're having with the system try and minimizing is just an option in utorrent for what the close button does.  Look around in the settings.

---

### Post by srunni on 2006-08-29
To fix your problem of only the window edge appearing, go to preferences and disable minimze to tray. It doesn't work, and neither does close to tray, so turn that off too. I would suggest enabling "single-click on tray icon to open" and using that instead.

---

### Post by 13east on 2006-08-29
thx srunni (and cable), that solved everythin
no more prblms with any of the graphical glitches

---

### Post by magnifica on 2008-01-18
> **srunni said:**
> To fix your problem of only the window edge appearing, go to preferences and disable minimze to tray. It doesn't work, and neither does close to tray, so turn that off too. I would suggest enabling "single-click on tray icon to open" and using that instead.

Cheers Srunni.  That works a treat for fixing the maximise bug.

---

### Post by Shimmy on 2008-01-18
Why don't just run deluge-torrent?
> sudo apt-get install deluge
It's very similar to utorrent

---

