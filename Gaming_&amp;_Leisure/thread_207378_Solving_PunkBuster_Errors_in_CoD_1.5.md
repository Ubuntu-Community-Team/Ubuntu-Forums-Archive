---
title: "Solving PunkBuster Errors in CoD 1.5"
date: 2006-07-01
forum: Gaming &amp; Leisure
---

### Post by berserker on 2006-07-01
I solved my various "Insufficient O/S Privileges" and "No Packet Flow" errors while running Call Of Duty 1.5 using Wine on PunkBuster-enabled servers.

Download pbsetup.exe from [here]("http://websec.evenbalance.com/downloads/windows/pbsetup.exe").

I had to change ownership of the CoD directory to my user (user in the below example):
```
sudo chown -R user:user /usr/local/games/cod
```

Run pbsetup.exe:  ```
wine pbsetup.exe
``` select Call of Duty and point it to your CoD directory (e.g., /usr/local/games/cod).  Run the update to install PunkBuster.

Run Wine config:
```
winecfg
```

Add application:
```
/usr/local/games/cod/CoDMP.exe
``` and select Windows 98 as the Windows Version.

Run CoD and it should work.

---

