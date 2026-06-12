---
title: "Dota 2 causes comp to crash"
date: 2014-10-20
forum: Gaming &amp; Leisure
---

### Post by Hastur_The_Unspeak on 2014-10-20
The issue is as follows- Today I went to boot up my comp. It gave me some weird ata5.00 error on bootup. After updating, it gave me the same message a few more times, then it went away. This is likely unrelated to my dota issue, but I felt I should state it for sake of detail. Anyhoo, I went to play dota on steam. Everything booted up just fine, then, all of a sudden, this weird crackly sound started to play through my headset. Then my comp crashed to a screen with nothing but my cursor and wallpaper on it. I shutdown my comp. Trying to duplicate the error, I booted up my comp and went into dota again. Roughly 5 minutes in, I crashed again. I also tried playing starcraft 2 on wine, and a few other games. All of them worked fine. The massive increase of fan speed and system toll was not present in this as it was in dota. I decided to do some digging for crash logs, and this is what I found. 
```

ERROR: apport (pid 2723) Sun Oct 19 18:38:53 2014: called for pid 2568, signal 11, core limit 0
ERROR: apport (pid 2723) Sun Oct 19 18:38:53 2014: executable: /home/vincent/.steam/steam/SteamApps/common/dota 2 beta/dota_linux (command line "/home/vincent/.steam/steam/SteamApps/common/dota\ 2\ beta/dota_linux")
ERROR: apport (pid 2723) Sun Oct 19 18:38:53 2014: executable does not belong to a package, ignoring
ERROR: apport (pid 5238) Sun Oct 19 22:25:35 2014: called for pid 4329, signal 11, core limit 0
ERROR: apport (pid 5238) Sun Oct 19 22:25:35 2014: executable: /home/vincent/.steam/ubuntu12_32/steam (command line "/home/vincent/.steam/ubuntu12_32/steam")
ERROR: apport (pid 5238) Sun Oct 19 22:25:35 2014: executable does not belong to a package, ignoring

```
Any help is appreciated.

---

