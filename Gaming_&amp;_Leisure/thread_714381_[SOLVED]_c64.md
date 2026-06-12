---
title: "[SOLVED] c64"
date: 2008-03-03
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-03
Hi,
I own a C64 and many tape games at home.
So I would say it is perfectly legal for me to use a C64 emulator.

I finally got a C64 emulator installed with this guide:
[http://aparateys.blogspot.com/2007/06/running-vice-121-commodore-emulator.html](http://aparateys.blogspot.com/2007/06/running-vice-121-commodore-emulator.html)

One big question though - How do you actually get a game to run?

I know in the terminal you type ```
x64
``` to open the emulator and you can left click to bring up menu items. I just don't know how to run a game.

I had a C64 emulator on my Xp install - I am using the games from this to try and play in Linux Vice C64 emulator.

Please help if you can.

Thanks.

---

### Post by DoktorSeven on 2008-03-03
Fastest way is to leftclick->Smart-attach disk/tape.... (or alt+a).

Then browse to the tape or disk image, and hit Autostart in the file dialog.

Slow way is Attach Disk Image->Unit 8 (alt+8 ), then do CBM BASIC commands to load:
LOAD "*",8 (enter, wait)
RUN

or 
LOAD "*",8,1
(for autostarting programs)

For tape images, left-click, Attach Tape Image, then

LOAD (enter, wait)
RUN

---

### Post by Rytron on 2008-03-04
thanks DoktorSeven.

i used your method

[COLOR="DarkGreen"]Fastest way is to leftclick->Smart-attach disk/tape.... (or alt+a)[/COLOR].

How about joypad controls? I tried getting them to work - no luck.

---

### Post by vpsville on 2008-03-04
Didn't know you could do that.  Amazing.  I'll have to dust off my c64 games collection.

Those games were the best!

---

### Post by Rytron on 2008-03-04
there is no problem with any games I have tried so far.
the sound is correct.

what are the keyboard buttons to use?
in some games it is z,x,uparrow. in other games i cant get any keyboard control.

also I'd really appreciate it if someone could explain how to set up the joystick settings. 

cheers.

ps I am now truly in awe of Ubuntu - as I am figuring out to use all my favourite applications and games from windows in the ubuntu - the step from windows to ubuntu is getting easier.

---

### Post by Rytron on 2008-03-04
Eureka

I just figured it out.

Depending on the game
- right click on x64 emulator
- joystick settings-
- port 1/2 select analogue joystick 0 and have other as 'none'

Enjoy those classic C64 games once more on the might Linux.

:KS

---

