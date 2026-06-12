---
title: "Steam installing error"
date: 2006-09-15
forum: Gaming &amp; Leisure
---

### Post by DiJEH on 2006-09-15
Following the Linux-gaming guide I'm trying to install Steam but having problems. I get as far as updating Steam (26% crash ahoy). Try to do the fix but get the following in Terminal.

stephen@Stephen:~$ wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found

Anyone know how to got a fix for a fix..?

---

### Post by Iarwain ben-adar on 2006-09-15
Hi,
normally one would type
```
wine "C:\Program Files\Steam\SteamTmp.exe" Selfupdate "C:\Program Files\Steam\Steam.exe" 14
```

Try that ;)


Iarwain

---

### Post by DiJEH on 2006-09-15
I can't remember how big I did managed to find a way round it by changing the location around in some way. Now just leeching things :)

Thank you for the help though, maybe it'll come in handy next time.

Edit :

Now Steam crashs after a couple of minutes, I'm not sure if it's loading TFC or if it's just Steam it's self. Anyone have exprience with it?

---

