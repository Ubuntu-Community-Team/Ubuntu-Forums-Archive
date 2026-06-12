---
title: "Does anyone have TC:E .49 working?"
date: 2006-09-29
forum: Gaming &amp; Leisure
---

### Post by SolidAndShade on 2006-09-29
The newest version (0.49) of Enemy Territory mod TrueCombat:Elite was released today. Does anyone have it working properly in Ubuntu? I can't connect to servers or host my own game without major problems.

When I try to connect to a server, it'll usually prompt me to download pak0.pak3, pak1.pak3, and other map files that I already have. Sometimes that won't happen and I'll see a loading screen, but then it'll disappear and I'll be dumped back to the beginning menu.

WHen I try to host a game, I'm able to create and join it all right, but if I crouch or jump the game instantly freezes and dumps me at the main menu.

I'm running Dapper with integraded geForce6500 graphics and an nForce 4 chipset. Thanks for any tips you can offer.

---

### Post by aidanr on 2006-09-30
make sure you join obj_ games and not dem_ games, because they are 0.48
also do a clean install of 0.49, don't just overwrite 0.48

it's been going pretty good for me so far apart from the firebug that some people have been getting, when someone fires their weapon ingame, most of the time the game stutters really bad and 99% of the time ends up getting you killed

---

### Post by finnjimm on 2006-09-30
Sorry for thread hijack but does anyone know a working torrent for Linux version? Or does the regular *.zip package work with Linux version of ET? Then I can tell if it works with me :)

---

### Post by Perfect Storm on 2006-09-30
I'll be able to tell in 30 min when I'm done downloading.

---

### Post by halfvolle melk on 2006-09-30
Yep, runs nicely. Might be needed to remove 0.48 first. But a clean install from ET up works nicely.

---

### Post by gaminggeek on 2006-09-30
Works for me.

---

### Post by =Kevin= on 2006-09-30
Heeyy,

I just installed the 0.49 version too, installation went fine and such. 
However If I run the game, I can see the menu background but not the menu itself :( 

Is this a known problem with .49?

-Kevin

---

### Post by NickeM on 2006-09-30
I have the firefight lag issue too, have you found a solution to this? someone mentioned that it might be a server issue but the from what i hear the windows clients doesn't have this problem.

---

### Post by aidanr on 2006-09-30
someone posted a fix that worked for me, in the options turn off wallmark lifetime, worked a treat, silky smooth now:D

---

### Post by Matt Yun on 2006-09-30
I downloaded the Linux binary from here:

wget [http://hydrogen.cert.ucr.edu/ftp/pub/mitch/true.combat.elite_0.49-english.run](http://hydrogen.cert.ucr.edu/ftp/pub/mitch/true.combat.elite_0.49-english.run)

I had to completely uninstall the entire Enemy Territory installation, not just TCE, because the main menu wasn't loading.  I reinstalled ET from my et-linux-2.60.x86.run and et-linux-2.60-update.x86.run files (you can find both at [http://ftp.games.skynet.be/pub/wolfenstein/](http://ftp.games.skynet.be/pub/wolfenstein/))

Then:  chmod 755 true.combat.elite_0.49-english.run && ./true.combat.elite_0.49-english.run

This thread was helpful:  [http://www.truecombat.us/forums/viewtopic.php?t=1009](http://www.truecombat.us/forums/viewtopic.php?t=1009)

---

### Post by NickeM on 2006-10-01
> **aidanr said:**
> someone posted a fix that worked for me, in the options turn off wallmark lifetime, worked a treat, silky smooth now:D

Tnx man, that really worked :D, i'll spread the word, and of course i'm off gaming too ;-)

---

### Post by =Kevin= on 2006-10-01
Thanks Matt Yun, your solution helped me ^^

I can play it now, but I think the new 'cinematic'  look is kind of strange... :???: 

-Kevin

---

### Post by NickeM on 2006-10-01
> **=Kevin= said:**
> Thanks Matt Yun, your solution helped me ^^

I can play it now, but I think the new 'cinematic'  look is kind of strange... :???: 

-Kevin

You get a broader field of view, ie. more realistic :) i thought the same as you but it grows on you, total immersion here i come ;-)

---

### Post by =Kevin= on 2006-10-01
You're right, I played the game some more and now I really like the new look aswell :)

Fun stuff :)

---

### Post by machia on 2006-10-02
Anyone got problems with the maps "snow & railroads"? I get "ERROR: Hunk_AllocateTempMemory: failed on 375880" -error. Someone suggested in the tce-website to config the autoexec.cfg -file (../et/tcetest/) so that the line "seta com_hunkMegs "512"" is half the RAM on ones system. This didnt work for me so I'm asking anyone got them to work with out crashing?

I also got weird un-rendered places in the other maps. In "Delta" the whole sky is black with orange lines and in the "Village" the center grass is full of pyramid shaped black/orange-thingys..
**update** it solved the un-rendering thing when I deleted everything from /home/../.etwolf/tcetest/

Anyone got any ideas?

I haven't tried to uninstall all (et&tce)..yet.

---

