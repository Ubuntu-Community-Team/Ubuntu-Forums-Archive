---
title: "Help, Can&quot;t Find Steam!"
date: 2007-07-17
forum: Gaming &amp; Leisure
---

### Post by sunami900 on 2007-07-17
OK I got into the code a little and I have it to where its all installed and i can't find steam newhere in apps or places or anywhere.. so i use code to bring up program right.. well it starts to update and then it just stops at 26% and says steam is already running. so where do i find this at!!??

---

### Post by dfreer on 2007-07-17
By default, it should be installed to a virtual c:\ drive, this is all located in your home folder.
```
~/.wine/drive_c/Program\ Files/Steam/steam.exe
```
This is where it is located on my system, as long as you didn't change the install paths it should be there. You can run it with a command like this:
```
wine ~/.wine/drive_c/Program\ Files/Steam/steam.exe
```

The glitch of stopping at 26% used to be a common problem, I believe it has several solutions listed at [http://appdb.winehq.org](http://appdb.winehq.org) Are you using the latest steaminstall.exe and the latest wine?

---

### Post by sunami900 on 2007-07-17
Solved

---

### Post by chuckyp on 2007-07-17
If you want steam to be in your Applications menu....

Double check first that its not under Applications > Wine > Programs > Steam.
If it isn't just open a console and type in wineboot.  This will start allt he programs that are supposed to start with windows as well as recreate your menu icons.

---

