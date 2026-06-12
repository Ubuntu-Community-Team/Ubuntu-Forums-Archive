---
title: "MAME Installation issues"
date: 2015-09-06
forum: Gaming &amp; Leisure
---

### Post by rolfUser on 2015-09-06
I tried installing MAME to my machine, and I had a minor misunderstanding with the ROMS/ISOs.

I went here for a guide to installation: [http://www.upubuntu.com/2012/10/how-to-install-mame-multiple-arcade.html](http://www.upubuntu.com/2012/10/how-to-install-mame-multiple-arcade.html)
Followed instructions that were included in the video, since I use Ubuntu 14.04 LTS.
Went here to download the games:
[http://coolrom.com/roms/mame/11500/Street_Fighter_III:_New_Generation_(Euro_970204).php](http://coolrom.com/roms/mame/11500/Street_Fighter_III:_New_Generation_(Euro_970204).php)
[http://coolrom.com/roms/mame/11516/Street_Fighter_III_2nd_Impact:_Giant_Attack_(USA_970930).php](http://coolrom.com/roms/mame/11516/Street_Fighter_III_2nd_Impact:_Giant_Attack_(USA_970930).php)

Typed this up```
**sudo ****nautilus /usr/local/share/games/mame/roms**
```
Then I dragged the zip files into the directory, extracted the files using Archive Manager (assuming this is what should be done) and then  I started up MAME.  The games were listed, but I got this weird error message.  I have it attached to this message. 
What is going on here? What am I doing wrong and how can I fix this issue?
[ATTACH=CONFIG]264264[/ATTACH]

---

### Post by MikeCyber on 2015-09-07
I have them in another directory and with user permissions working fine:

michael@michael-ubuntu:/usr/share/games/mame/roms$ ls -la
total 21256
drwxr-xr-x 2 root    root        4096 Apr 23 17:28 .
drwxr-xr-x 5 root    root        4096 Apr 24 10:24 ..
-rw-rw-r-- 1 michael michael  1419821 Jun 21  2010 1941.zip
-rw-rw-r-- 1 michael michael   759124 Jan 31  2015 88games.zip
-rw-rw-r-- 1 michael michael    69383 Jun 21  2010 arkanoid.zip
-rw-rw-r-- 1 michael michael    10848 Jun 21  2010 astdelux.zip
-rw-rw-r-- 1 michael michael     7264 Jun 21  2010 asteroid.zip
-rw-rw-r-- 1 michael michael  1619862 Jan 31  2015 batman.zip
-rw-rw-r-- 1 michael michael    20757 Jun 21  2010 btime.zip
-rw-rw-r-- 1 michael michael    31177 Jan 27  2015 ckong.zip
-rw-rw-r-- 1 michael michael    29784 Jun 21  2010 digdug.zip
-rw-rw-r-- 1 michael michael    42504 Jun 21  2010 dkong3.zip
-rw-rw-r-- 1 michael michael    30515 Jun 21  2010 dkongjr.zip
-rw-rw-r-- 1 michael michael    22302 Jun 21  2010 dkong.zip
-rw-rw-r-- 1 michael michael    24396 Jun 21  2010 galaga.zip
-rw-rw-r-- 1 michael michael 13222269 Jan 31  2015 gigawing.zip
-rw-rw-r-- 1 michael michael    47956 Jan 31  2015 hcastleo.zip
-rw-rw-r-- 1 michael michael  3087018 Jan 31  2015 hotpinbl.zip
-rw-rw-r-- 1 michael michael     5388 Jun 21  2010 invaders.zip
-rw-rw-r-- 1 michael michael    28399 Jan 31  2015 mappy.zip
-rw-rw-r-- 1 michael michael    21791 Jul 19  2010 mspacman.zip
-rw-rw-r-- 1 michael michael     2678 Jul 17  2010 mspacmat.zip
-rw-rw-r-- 1 michael michael   716099 Jul 19  2010 p47.zip
-rw-rw-r-- 1 michael michael    41260 Jan 28  2015 popeye.zip
-rw-r--r-- 1 michael michael   119000 Apr 23 17:24 ppmast93.zip
-rw-rw-r-- 1 michael michael    20677 Jul 17  2010 scobra.zip
-rw-rw-r-- 1 michael michael    15625 Jun 21  2010 scramble.zip
-rw-rw-r-- 1 michael michael   254035 Jan 31  2015 shinobi4.zip
-rw-rw-r-- 1 michael michael    26924 Jun 21  2010 vanguard.zip
michael@michael-ubuntu:/usr/share/games/mame/roms$ pwd
/usr/share/games/mame/roms
michael@michael-ubuntu:/usr/share/games/mame/roms$

---

### Post by rolfUser on 2015-09-08
I went here: [http://www.emuparadise.me/M.A.M.E._-_Multiple_Arcade_Machine_Emulator_ROMs/Street_Fighter_III:_New_Generation_(USA,_970204)/16456](http://www.emuparadise.me/M.A.M.E._-_Multiple_Arcade_Machine_Emulator_ROMs/Street_Fighter_III:_New_Generation_(USA,_970204)/16456)

I downloaded the CHD image. I created a file folder of the same name as the zip file and put the CHD image into the file folder. Then I cleaned out the rom path to start over and put these two folders instead. It worked out this time.

I was wondering. On startup, the game performed some kind of installation. This ran for almost 45 minutes.    I did this create a new file? if it did, I can't find it and the size of the chd file remained the same.    Is there any way to bypass this long process? 
      Also, an error message popped up saying that the old files were not dumped properly. I'm not sure why the machine would even notice. Also, there were errors saying that the game would function at 100%. As I played it, I noticed the sound went astray at times, but otherwise, it worked out. 

Is any of this normal? I'm just new to emulators.

---

### Post by MikeCyber on 2015-09-09
No it starts in  some seconds.
I've simply dropped the zips from:
[http://www.mameroms.com/](http://www.mameroms.com/)
into that location. Mame is from synaptic. No unzip or whatsoever, simply chmod 755 *, chgrp, chown to username.
I would get rid of that, 45 min...is insane maybe some kind of rootkit.- Never ever use sudo for install!

---

### Post by rolfUser on 2015-09-09
> **MikeCyber said:**
> No it starts in  some seconds.
I've simply dropped the zips from:
[http://www.mameroms.com/](http://www.mameroms.com/)
into that location. Mame is from synaptic. No unzip or whatsoever, simply chmod 755 *, chgrp, chown to username.
I would get rid of that, 45 min...is insane maybe some kind of rootkit.- Never ever use sudo for install!

I only used sudo to install mame itself.
the 45 minute installation, that is something the happened within the game itself -- both street fighter games.


What else is interesting is that I tried downloading Metal Slug, the first one. I put the zip file into the roms path.  The game pops up, but I got the exact same error message as before -- the one I posted as a screenshot.

What is interesting is that the links providing the zip file do not provide a chd file to go along with it.  So how am I supposed to get this game to boot?

---

### Post by MikeCyber on 2015-09-09
only put the zip into that directory. nothing else. all my zips work fine, no problems or complicated install. Some downloads are broken, deleted, done.

The simple old pong game, like in the movie "The Core" is pretty hard to play. Play against pc possible?
Thanks

---

### Post by rolfUser on 2015-09-10
What could be causing the error message?
More importantly, I think, what needs to be in the zip file?

---

