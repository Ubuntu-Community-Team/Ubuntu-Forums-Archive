---
title: "Winetool struggles"
date: 2006-08-14
forum: Desktop Environments
---

### Post by jharbert on 2006-08-14
I am trying to set up wine on Dapper as there are a few windows programs that I use regularly (and would prefer not to have to boot into windows just to use those programs).  I installed wine 0.9.5 (recommended for using winetools) and winetools.  Winetools started up fine and I was able to create the fake windows drive with no problems.  However when I go to install DCOM98, after agreeing to the licenses, it freezes on me.  I've tried going away from the computer for a few minutes to see if it was just being slow but still no luck.  This is what the terminal reads as it's frozen:

```
detecting Wine version... done.
Drive C: is /home/jharbert/.wine/drive_c
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
Calls to wine are executed as  "wine".
Config is /home/jharbert/.wine/winetools.log.
Choice is Base setup
Choice is DCOM98 with checked=F
dcom98.exe to check
software installation verified by /home/jharbert/.wine/winetools.log
1229056 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
waiting for wineservers to exit...

```

I've tried reinstalling both wine and winetools and I still get the same results.

If you know of any howtos that show how to install all of the same stuff that winetools does that would work as well.

Thanks,
Joshua

---

### Post by BLTicklemonster on 2006-11-09
I don't think you have to have dcom98, not really sure. Try the link in my sig. I'm having problems, too, btw.

---

