---
title: "X sever constantly restarts. THIS IS RIDICUKOUS xgl problem? (Kubuntu)"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by Smatt454 on 2008-02-06
First off i am running Kubuntu 7.10. glx works just fine. Now i have been trying forever to get compiz to work. (silly me didnt instally Xgl)

after i installed Xgl my font got a lot smaller (i was running a 800x600, either that my graphics card's max res or i have a serious problem, because thats another issue i dealed with for a while) and my system started to lag real bad. my cursor was REALLY laggy, sometimes it would be invisible (moving it around for a while brought it back) or sometimes it would mess up my graphics, like this
[IMG]http://img227.imageshack.us/img227/2443/snapshot2ny1.png[/IMG]

these problems seemed to be made better by starting compiz. (every 9/10 times) however about 1/10 times compiz worsened the problem 

the worst of these problems was that my x server would restart whenever i was typing. ONLY if was typing. it restarted less frequently (between every 5 and 20 mins) when compiz was running, but more frequently when it was not running (it happened 3 times in a row once, and would usually occur every 1-2 mins)

i have no idea what the problem is. i tried reinstalling my drivers, but this did not fix the problem. currently i have my drivers disabled, and of course nothing is lagging and the x sever does not restart. let me stress that BEFORE i installed xgl, everything worked fine WITH the drivers enabled.

this problem really bugs me, especially after i spent so long getting compiz to work. MY X SEVER ONLY RESTARTS WHEN I AM TYPING. MY COMPUTER LAGS EITHER WAY, BUT TYPING SEEMS TO WORSEN THE LAG AND CAUSES AN X SEVER RESTART!

i am running a penium 4 (1.80 Ghz) with 512 MB of RAM.  my graphics card is a Nvidia Geforce 256 

PLEASE HELP! i would hate to waste all that effort getting compiz to run. PLEASE do NOT tell me to use google. i really need SPECIFIC advice as i am relatively new to linux (5 months) and i have no idea how to fix this problem)

---

### Post by FuturePilot on 2008-02-06
Remove XGL. You don't need it if you have a Nvidia card.

---

### Post by Smatt454 on 2008-02-06
i unintstalled Xgl, now i get this error when i try to start compiz
```
~$ compiz --replace&
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0101 (rev 10) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

```

---

### Post by FuturePilot on 2008-02-07
I'd have to guess that something is wrong with your driver installation. Perhaps try reinstalling it.

---

### Post by Smatt454 on 2008-02-07
i did, through a few different methods

---

