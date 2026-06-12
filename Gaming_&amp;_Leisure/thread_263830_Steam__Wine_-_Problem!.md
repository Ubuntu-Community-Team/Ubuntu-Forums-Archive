---
title: "Steam / Wine - Problem!"
date: 2006-09-23
forum: Gaming &amp; Leisure
---

### Post by delta99 on 2006-09-23
hello

been trying now for 6-7 hrs to get steam up and running. I have managed to solve the last few problems thank god but sadly I cannot solve this one.

I am wondering if someone knows what my problem is and how to fix it! I would be most grateful!

[U]
The Terminal[/U]
```
delta@delta-desktop:~/.wine/drive_c/Program Files/Steam$ wine steam.exe
fixme:ras:RasEnumConnectionsW (0x7b2a5c50,0x7ad1e76c,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:ras:RasEnumEntriesW ((nil),(null),0x7b2db290,0x7ad1e434,0x7b2da38c),stub!
fixme:actctx:CreateActCtxW stub!
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
fixme:nls:CompareStringW Ignoring unknown style 0x10000000
Unable to remove c:\program files\steam\shortcuts.dat!
Shutting down. . .
9delta@delta-desktop:~/.wine/drive_c/Program Files/Steam$

```

Thanks :)

---

### Post by infoburner on 2006-09-23
as far as the lack of text goes, you need mozcontrol for wine. [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine&back=HOWTO+INDEX+Wine](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine&back=HOWTO+INDEX+Wine)
scroll down to number 6.

---

### Post by Zubenelchenubi on 2006-09-23
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

I don't know what your error means but have you seen this link already? You can start with installing tahoma font.

---

### Post by claydoh on 2006-09-23
I don't know what is causing your problem, but I just today installed steam using the latest wine (0.9.21)

Add this line to your sources.list:
deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) dapper main

there is more info at [http://www.winehq.com/site/download](http://www.winehq.com/site/download)
but the site seems down atm

I installed that, plus msttcorefonts (not sure if they were necessary though), deleted my .wine folder, and simply double-clicked on the steam installer .exe. It automatically restarted at the dreaded 26% hang, and finished the install, and even automatically asked to install the Mozilla html engine before steam opened up :)

the only difficult part is entering your steam username/password, as you need to left-click in the form box, then right-click in it to get the correct focus ( or was it the other way 'round?).Be sure to check the "remember" box so you don't have to do this every time you run it. Aslo, once you have the big steam window open, you need to close it before a game loads up or it will stay on top of your window no matter what you do.

I installed Half Life 1 so far, and it seems to run just as well as it does in cedega for me, outside of the two items above. The steam interface imo actually runs smoother there for me than in cedega.

I have not yet innstalled any of my other games to see how they run just yet, however.

---

### Post by delta99 on 2006-09-24
Thanks all! it worked!

I installed Mozcontrol/FFDShow/Tahom.tff and I can now execute steam.

But your right though, I couldn't close steam... just gotta download css now :)

awesome thx

---

