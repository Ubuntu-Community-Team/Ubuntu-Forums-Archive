---
title: "WINE not recognising CD?"
date: 2006-08-19
forum: Gaming &amp; Leisure
---

### Post by Maelgwyn on 2006-08-19
I know this has probably been covered before, so sorry in advance!

I've just installed Diablo II: LOD via wine on Ubuntu 6.06 and the install went smoothly.. However, when I try to play it, I get an error message saying that there is no Play CD in the drive! I've tried to 

```

wine /media/cdrom/playd2.exe

```

but I still get the same error *sigh*

Can somebody help me get around this?

Also, are there any issues playing Multiplayer over a LAN? My flatmate is running WinXP and we'd like to play Diablo II together... :)


Thanks!!8)

---

### Post by slimdog360 on 2006-08-19
I dont know but maybe a no cd patch would work?

---

### Post by Maelgwyn on 2006-08-19
Do I need WINE-specific ones? Where do I get one? Sorry, I'm such a n00b sometimes... :rolleyes:

---

### Post by frup on 2006-08-19
have you looked at frankscorner.org to see if theres any good info?

> Tested Wine version: 20030813

-Type wine /pathtocdrom/install.exe to install Diablo 2.

-After installing copy d2music.mpg from the Play-CD to the installation directory of the game.

-Download the 1.09b patch and install it (wine D2Patch_109b.exe).

-Go to [www.megagames.com](www.megagames.com) and download a cracked .exe. Rename this file to Game_crack.exe and copy it to the Diablo 2 installation directory.

You can now play Diablo 2 by typing wine Game_crack.exe in the installation directory.


To play on Battle.net you need a script:

#!/bin/sh
mv -f Game.exe Game1.exe
mv -f Game_crack.exe Game.exe
wine "Game.exe" &
sleep 2
mv -f Game.exe Game_crack.exe
mv -f Game1.exe Game.exe
exit

Save the script as diablo.sh
Now start Diablo 2 by typing sh diablo.sh 

---

### Post by scotty2hott2k on 2006-08-19
wine doesn't support the required functions (such as in ntkernel.exe) to enable copy protection to work for games.

---

### Post by Anduu on 2006-08-19
Run wincfg and make sure your cdrom path is correct.

---

### Post by Maelgwyn on 2006-08-20
> **Anduu said:**
> Run wincfg and make sure your cdrom path is correct.

But what's "correct"? I've got both /media/cdrom & /media/cdrom0/ mapped...

Also, I couldn't find the 1.09b patch, so downloaded the 1.11b patch instead but it said it couldn't find a file... d2exp.mpq ? I tried touching a file with the same name, but that didn't work...

---

### Post by Anduu on 2006-08-20
> **Maelgwyn said:**
> But what's "correct"? I've got both /media/cdrom & /media/cdrom0/ mapped...

Also, I couldn't find the 1.09b patch, so downloaded the 1.11b patch instead but it said it couldn't find a file... d2exp.mpq ? I tried touching a file with the same name, but that didn't work...

Either or should work but not both...(ie remove one of them).Also be sure it is assigned the correct drive letter...typically D:

To install the patch copy it directly into .wine/drive_c/Program Files/Diablo II folder and run it from there.

---

### Post by Anduu on 2006-08-20
Here is what my drives section in winecfg looks like...Yours obviously should be /media/cdrom/

---

### Post by Maelgwyn on 2006-08-20
Awesome - thanks heaps! It works, but it's UBER slow... I'll see if a no-cd crack works, so it's not accessing the CD drive, 'cause it's only a 24x lol

---

### Post by Anduu on 2006-08-20
> **Maelgwyn said:**
> Awesome - thanks heaps! It works, but it's UBER slow... I'll see if a no-cd crack works, so it's not accessing the CD drive, 'cause it's only a 24x lol

What are your system specs?

I run it on a 1.8 Ghz Athlon XP and it is very playable...not as fast as Windows but still fine.

Sounds like you need to do a full install so as to eliminate the need to read from the CD...you still need the disk in the drive to play tho.I know it takes a lot of HD space but it is well worth it.

---

### Post by HAARP on 2006-08-20
> 
-Go to [www.megagames.com](www.megagames.com) and download a cracked .exe. Rename this file to Game_crack.exe and copy it to the Diablo 2 installation directory.

You can now play Diablo 2 by typing wine Game_crack.exe in the installation directory.


To play on Battle.net you need a script:

#!/bin/sh
mv -f Game.exe Game1.exe
mv -f Game_crack.exe Game.exe
wine "Game.exe" &
sleep 2
mv -f Game.exe Game_crack.exe
mv -f Game1.exe Game.exe
exit

Save the script as diablo.sh
Now start Diablo 2 by typing sh diablo.sh

Sorry for ranting, but what the hell is this crap? Just rename the original one Game.exe_old or something and name the crack Game.exe. No scripts.

And please don't use cracks for old versions with a new version. Thanks.

---

### Post by Anduu on 2006-08-20
> **HAARP said:**
> Sorry for ranting, but what the hell is this crap? Just rename the original one Game.exe_old or something and name the crack Game.exe. No scripts.

And please don't use cracks for old versions with a new version. Thanks.

Hate to say it but I did absolutely nothing special besides installing the patch to be able to play online...

---

