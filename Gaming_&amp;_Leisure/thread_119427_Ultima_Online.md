---
title: "Ultima Online"
date: 2006-01-19
forum: Gaming &amp; Leisure
---

### Post by chronusdark on 2006-01-19
is there a native linux UO client and if so where can i get it?

i just got the game the other day and it kinda works in wine but i cant get the 3d client to work

thanks in advance

---

### Post by Zodiac on 2006-01-19
UO in 3D SUCKS! 

If I were you I would stick with the 2D dawg...

---

### Post by chronusdark on 2006-01-20
well then 2 more questions

1. is there a way to get uogateway to work?
it doesnt want to load with cedega and wine gives me errors

2. is there a way to close the Ultima online is loading window when playing with wine??

---

### Post by jon_z on 2006-01-20
to completely kill ultima online when running with wine, in a console:

```
killall -9 wine-preloader
killall -9 winserver
killall -9 wine
```
Should make sure that the program is closed.

---

### Post by Asraniel on 2006-01-20
there are clients like ultima iris... never tried it, but looks nice

---

### Post by postmoderntool on 2007-10-21
in terminal 

```
[SIZE="4"]killall -9 uo.exe[/SIZE]
```

That worked for me.

---

### Post by Amaroq on 2007-11-26
WineHQ's appdb says:
"Instead of loading uo.exe, load client.exe.  When you need to patch load uopatch.exe."

That fixes the loading window issue.

I'm trying to get UOGateway to work as well. Anybody got that working yet?

---

