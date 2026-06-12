---
title: "Counter Strike and Steam"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by whitefeather160 on 2007-06-03
When i load steam it doesnt give me any text

[IMG]http://i15.tinypic.com/5xxb8mq.png[/IMG]

what do i do

---

### Post by Alex Fernandez on 2007-06-03
Install tahoma font within wine.

Either put tahoma.ttf into the windows fonts dir or find a tahoma.exe and run it (wine tahoma.exe)

---

### Post by whitefeather160 on 2007-06-03
i downloaded the tahoma.exe already and did $wine tahoma.exe, i assumed the text it gave me meant success.  it still isnt working...

---

### Post by sonicborg on 2007-06-03
i have those fonts in /usr/share/fonts/truetypes/custom fold (i am sure i read to put it there somewhere) and i dont get that problem. i did when i first tried to install the game.

also might be worth going into .wine directory and putting them in windows/fonts maybe.

---

### Post by Syahmi on 2007-06-03
Download the tahoma font file which is tahoma.ttf I believe and put in inside the /windows/font/ folder and then restart Steam.

---

### Post by sonicborg on 2007-06-03
yep yep,

problems i have had this weekend......

had to step back to wine .37 to get a proper install (.38 always stuck on updating steam)

Failing to load due to reg already being used. (this is solved by loading steam, clicking properties of CSS, verify integrity of files) onces that complete, load the game from steam menu

Blank screen when game loads in menu (this is solved by properties of game, launch options put in '-dxlevel 70') (i actually found 90 had better frame rates)

now just gotta sort out the frame rate. feels like i am playing on a 14.4k modem right now cause of this frame rate

---

