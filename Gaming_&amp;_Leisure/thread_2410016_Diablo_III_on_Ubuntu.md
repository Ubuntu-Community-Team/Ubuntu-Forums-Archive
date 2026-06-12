---
title: "Diablo III on Ubuntu?"
date: 2019-01-10
forum: Gaming &amp; Leisure
---

### Post by kibiras on 2019-01-10
Hello. I found in Blizzard old topic about Diablo III on Ubuntu, but in comments many say that way is too old and not work. Maybe someone here can help me with that "How to install and run Diablo III on Ubuntu step by step?" :KS

---

### Post by oldrocker99 on 2019-01-10
Just looked, and Google doesn't anything wbout it. Install PlayOnLinux; it may well have a script for Diablo 2. 

It might not, either.

```
sudo apt install playonlinux
```

---

### Post by kibiras on 2019-01-10
Endless installation:

[ATTACH=CONFIG]282169[/ATTACH]

---

### Post by oldrocker99 on 2019-01-11
Well, some Windows games run very well with win, and some don't at all. I've had endless installations happen to me.

---

### Post by jamolver on 2019-01-14
There are tips, maybe you can help ....[https://ubuntuforums.org/showthread.php?t=2350866](https://ubuntuforums.org/showthread.php?t=2350866)

---

### Post by mastablasta on 2019-01-14
have you looked at wine HQ?: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=29952](https://appdb.winehq.org/objectManager.php?sClass=version&iId=29952)

---

### Post by kibiras on 2019-01-18
wine isn't working fine. It struck on installing.

---

### Post by mastablasta on 2019-01-18
well lotteries are known to be difficult to get a hit. otherwise everyone would be a millionaire :P it says on winHQ:

> 

[COLOR=#000000][FONT=&amp]***Installation is a lottery***, use previous script uploaded for another user, thanks a lot ( use if installation doesn't work, several tries ):[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]#!/bin/bash
killall Agent.exe
killall Battle.net.exe
rm -fR /%PATH-TO-PREFIX%/drive_c/ProgramData/Battle.net/Agent/product.db
sleep 5
echo Process complete
sleep 5
exit[/FONT][/COLOR]



[FONT=Verdana][/QUOTE][/FONT]

---

### Post by mistersynystyr23 on 2019-02-11
have you tried using Lutris? its really user friendly and i got overwatch to work a while back with it. heres a link to save you time [https://lutris.net/games/diablo-iii/](https://lutris.net/games/diablo-iii/)

---

### Post by peterkearns007 on 2019-02-12
I tried running Diablo 3 with PlayonLinux but did not manage to install it as well. Any other options?

---

### Post by oldrocker99 on 2019-02-12
> **mistersynystyr23 said:**
> have you tried using Lutris? its really user friendly and i got overwatch to work a while back with it. heres a link to save you time [https://lutris.net/games/diablo-iii/](https://lutris.net/games/diablo-iii/)

I had heard of Lutris, but only installed it on your recommendation. It's pretty sweet.

---

### Post by bred55 on 2019-02-14
> **peterkearns007 said:**
> I tried running Diablo 3 with PlayonLinux but did not manage to install it as well. Any other options?
Which Version of PlayonLinux you are using?

---

### Post by mastablasta on 2019-02-14
current play on linux available with 18.04 does not work well at all. manual wine install might be the way to go.

as alternative option - i am currently playing Torchlight (works out of the box in wine), while Torchlight 2 has linux client. i haven't played diablo3. i did play diablo2 and Torchlight is quite similar only much better.  and also way more fun. especially for kids. The only issue is Torchlight doesn't feature multiplayer (still you can give items to another character), however the second version "solved" that issue. anyway just throwing it out there as possible alternative time waster.

---

### Post by oldrocker99 on 2019-02-14
+1 on Torchlight II. It's a game I've played many hours. It's bigger and better than the original, and **highly** recommended.

By me.

---

