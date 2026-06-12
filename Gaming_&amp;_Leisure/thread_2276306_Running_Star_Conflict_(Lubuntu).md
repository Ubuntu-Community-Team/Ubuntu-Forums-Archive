---
title: "Running Star Conflict (Lubuntu)"
date: 2015-05-01
forum: Gaming &amp; Leisure
---

### Post by linux_dream on 2015-05-01
I've downloaded and installed Steam as well as Star Conflict. However when I tried to run the game a window would pop up and close instantly and the game wouldn't start. So I ran it from the terminal and apparently a lib was missing. After googling here and there I finally found out which lib was missing, turns out that there was a lot of missing libs...
Then there was another problem that I had to create a .txt file with the ID of the game (and had to use this website to find out the ID: [https://steamdb.info/search/?a=app&q=star+conflict](https://steamdb.info/search/?a=app&q=star+conflict))
So now I have fixed the missing lib problems +.txt problem and I now have another problem when I execute the program ```
./StarConflict 


```:
```
Setting breakpad minidump AppID = 212070
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198194439827 [API loaded no]
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  34 ()
  Serial number of failed request:  218
  Current serial number in output stream:  219
Segmentation fault (core dumped)
```
Is there a way I can fix that problem? My graphics card is a NVIDIA geforce 7300 GS.

---

