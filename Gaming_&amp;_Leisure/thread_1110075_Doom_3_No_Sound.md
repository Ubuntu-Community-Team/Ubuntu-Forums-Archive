---
title: "Doom 3 No Sound"
date: 2009-03-29
forum: Gaming &amp; Leisure
---

### Post by S0m3th1ngw13rd on 2009-03-29
Installed Doom 3 and it runs perfectly except no sound.
Tried a number of fixes in various forums but still nothing.
When I switch sound in game options to OSS and restart game it just goes to a black screen and stays there. This is also in terminal when it blacks out:

```
-----OSS Sound Initialization ------
opened sound device '/dev/dsp'
```


 Anyone available to help me troubleshoot? That would be greatly appreciated.

---

### Post by rizzeh on 2009-03-29
I've had problems with doom3 sound too.
what i did is - set doom3 to ALSA backend in game's options menu and reinstalled ALSA following this guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by S0m3th1ngw13rd on 2009-03-29
tried all that and still nothing thanks for the look though

---

### Post by S0m3th1ngw13rd on 2009-03-29
ok fixed now. My modules array in /etc/rc.conf had:

```
(!soundcore...)
```

removed that entry and set in game to alsa and works great!

---

