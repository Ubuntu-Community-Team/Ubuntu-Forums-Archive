---
title: "CS:S problems"
date: 2006-08-24
forum: Gaming &amp; Leisure
---

### Post by sunrex on 2006-08-24
Css.. the lag on this thing is killing me its like 1 frame per every 3 seconds, CS:1.6 runs fine!

i want your opinion on what to do, what windows version does CSS run best under in wine, and how would i solve the lag? i think its the fact its DX, but it might be my accel.

---

### Post by Mutch on 2006-08-24
Yer i feel your pain.
Are you running wine in debug mode? If i don't i get mega chug aswell
instead of ```
wine steam.exe
```

Try

```
WINEDEBUG="fixme-all" wine Steam
```

I followed this guide --> [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

Hope that helps

---

### Post by ivandeterrible on 2006-08-24
i would like to know how to instal counter strike 1.6 exe under ubuntu using wine

---

### Post by sunrex on 2006-08-24
you just use steam and install wine there.

---

### Post by sunrex on 2006-08-24
> **Mutch said:**
> Yer i feel your pain.
Are you running wine in debug mode? If i don't i get mega chug aswell
instead of ```
wine steam.exe
```

Try

```
WINEDEBUG="fixme-all" wine Steam
```

I followed this guide --> [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

Hope that helps

That helped, i get around 20-40 FPS now, most of the time its in the 30's.

now i have another question, the debug is good and all, but how would i combine these 2 commands as one? 

nice -n -20 wine "Steam.exe"

WINEDEBUG="fixme-all" wine Steam


nice -n -20 wine "Steam.exe" makes it so it has top priority on my cpu, but i cant seem to use it with WINEDEBUG="fixme-all" wine Steam, i want to use both.

---

### Post by sunrex on 2006-08-25
anyone know?

---

### Post by Mutch on 2006-08-26
Hmmmm

Im pretty sure i did that.
Opens Steam to test......

Hmmmm i can't seem to figure it out.
At least you get 20-40fps. My css just freezes :(

---

### Post by Mooie on 2006-08-26
in steam, right click on the game and then click on launch options.  try adding ```
-dxlevel 81
``` or ```
-dxlevel 70
``` if you have to.  after you launch the game w/ the new directx level, you will probably need to change your resolution and video settings to how you want, and after you exit you will need to delete the -dxlevel thing from your launch options.

also, I use ```
-heapsize 1024000
``` in my launch options, I use 1024000 because I have 2 gigs of ram, and you are supposed to use -heapsize with up to half your ram in kb.  I think it loads everything into my ram, which probably speeds it up.  if you have 512 mb of ram use ```
-heapsize 256000
``` 1 gig would be ```
-heapsize 512000
``` and so on.

hope it helps you.


I am getting problems loading the steam store, and the welcome to server picture/message things using wine (9.20 and the latest cedega)  I would like to figure out how to make it work in wine, but i cant find any threads on it...  any help would be appreciated

---

### Post by sunrex on 2006-08-26
Well im trying the cedega demo on this new install, unlike most, i am not against paying for things that work, but if all thats going to work on cedega is a game or two forget it.

---

### Post by sunrex on 2006-08-26
the demo was crap, how cedega is still out i will never know.

but has anyone got those two commands to work? i would really like to be able to have WINEDEBUG working with HIGH PRIORITY..

anyway, if no one can get it to work thats the end of this Thread.

-Sunrex.

---

