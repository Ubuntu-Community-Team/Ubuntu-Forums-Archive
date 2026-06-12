---
title: "Enemy Territory"
date: 2007-07-01
forum: Gaming &amp; Leisure
---

### Post by phizikal on 2007-07-01
Okay, alien arena and warsow gets really old. I don't like the "futuristic" and the alien stuff. I want a more realistic game and  something more military like. I heard about WolfenStein: Enemy Territory. Is this available for linux, and also is there a automatic installer ",deb" or if not can someone explain how to download and install. Please and thank yous.

---

### Post by Zimmer on 2007-07-01
[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

Should tell you all you need to know.
I have stopped playing as my new keyboard will not play nice .... something to do with the mapping of the keys...

---

### Post by aidanr on 2007-07-01
I'd also check out [True Combat Elite]("http://www.truecombatelite.net/"), an ET mod

---

### Post by phizikal on 2007-07-01
Yeah, I have the game correctly downloaded and installed. For some reason in isn't running. Could it not be available for dapper for what?

---

### Post by Zimmer on 2007-07-01
> **phizikal said:**
> Yeah, I have the game correctly downloaded and installed. For some reason in isn't running. Could it not be available for dapper for what?

Please explain... symptoms? 
Does nothing happen at alll?
How have you tried to start the game? Have you tried typing  et   in a terminal ?

Have you looked at the troubleshooting guide?

Need to sleep, it is 3am here.... look for other posts by me for ET if you get any further.. the problems are , graphics drivers , sound and permissions.

G'night

---

### Post by FoolsGold_MKII on 2007-07-01
> **phizikal said:**
> Okay, alien arena and warsow gets really old. I don't like the "futuristic" and the alien stuff. I want a more realistic game and  something more military like. I heard about WolfenStein: Enemy Territory. Is this available for linux, and also is there a automatic installer ",deb" or if not can someone explain how to download and install. Please and thank yous.
I know you're looking at ET, but since you mentioned "realistic and military like", I highly recommend a game called Urban Terror. It started off as a mod for Quake 3, but you can now download the game stand-alone without requiring Q3. It's pretty good, I play it more than ET and there's plenty of servers.

[http://www.urbanterror.net/](http://www.urbanterror.net/)

---

### Post by Darganot on 2007-07-05
Thanks for the link zimmer  :D

Fools gold, I have urban terror 4.0 installed and I can get the mod to run through open arena but no severs show up.  I'm stuck playing the older version in the open arena room.  Have you heard of this?

---

### Post by FoolsGold_MKII on 2007-07-05
> **Darganot said:**
> Thanks for the link zimmer  :D

Fools gold, I have urban terror 4.0 installed and I can get the mod to run through open arena but no severs show up.  I'm stuck playing the older version in the open arena room.  Have you heard of this?
Gah, you're doing it all wrong! :)

Urban Terror 4 can it as a mod if you wish, but this new version is designed to work better as a standalone game; in fact they highly recommend you do it as such and not run it as a mod in Quake 3 (or OA for that matter).

Here's what you do:

Go to the downloads page at [http://www.urbanterror.net/page.php?6](http://www.urbanterror.net/page.php?6) and download the linux version of **ioUrbanTerror** - this is the open-sourced Quake 3 engine customized for Urban Terror.

Unpack that somewhere, then move the UT mod folder out of your OpenArena folder and stick it in the relevant place in ioUrbanTerror. Run ioUrbanTerror and it should work.

Someone made a script for Linux to facilitate these steps if that makes things simpler:
[http://www.forums.urbanterror.net/index.php/topic,8165.0.html](http://www.forums.urbanterror.net/index.php/topic,8165.0.html)

---

### Post by Darganot on 2007-07-08
> **FoolsGold_MKII said:**
> Someone made a script for Linux to facilitate these steps if that makes things simpler:
[http://www.forums.urbanterror.net/index.php/topic,8165.0.html](http://www.forums.urbanterror.net/index.php/topic,8165.0.html)

Thanks man!  I followed the instructions, ran the script, everything downloaded ok and seemed to install fine.  But when I run urbanterror4 at the command I get this:
```

ioQ3 1.33urt linux-i386 Apr  2 2007
----- FS_Startup -----
Current search path:
/home/darganot/.q3a/q3ut4
/home/darganot/Games/UrbanTerror4/q3ut4/ut4_subway.pk3 (189 files)
/home/darganot/Games/UrbanTerror4/q3ut4/ut4_sliema.pk3 (335 files)
/home/darganot/Games/UrbanTerror4/q3ut4/ut4_paradise.pk3 (142 files)
/home/darganot/Games/UrbanTerror4/q3ut4/ut4_kotp.pk3 (15 files)
/home/darganot/Games/UrbanTerror4/q3ut4/ut4_arena2.pk3 (13 files)
/home/darganot/Games/UrbanTerror4/q3ut4/ut4_arena1.pk3 (13 files)
/home/darganot/Games/UrbanTerror4/q3ut4
/home/darganot/.q3a/baseq3
/home/darganot/Games/UrbanTerror4/baseq3

----------------------
707 files in pk3 files
Sys_Error: Couldn't load default.cfg

```

The .pk3 files seem to be in the correct directory and everything.  I'm not sure what else to do.

RTCW is running fine tho.

---

### Post by Darganot on 2007-07-12
Ah, never mind.   I  got the script to work fine by just deleting everything and running it again.  DL'ed fine and ran with the icon on desktop.  It's really laggy for me though.  I think I'll stick to et, I really like it.

---

### Post by cmat on 2007-07-12
Urban Terror is fun but it's graphics are extremely dated and game play gets old fast (or I just suck :) ). ET is fantastic but not really realistic, everyone can run 50 MPH and jump 10 ft in the air. True Combat : Elite is your best bet, it pushed the Enemy Territory engine to the limit and boasts some excellent game play. It's as realistic as you can make ET. It's development runs stagnant for long periods of time, but it is getting worked on. 

We need an open source battlefield like game based on ioquake3. :)

---

### Post by FoolsGold_MKII on 2007-07-13
> **cmat said:**
> Urban Terror is fun but it's graphics are extremely dated and game play gets old fast (or I just suck :) ). ET is fantastic but not really realistic, everyone can run 50 MPH and jump 10 ft in the air. True Combat : Elite is your best bet, it pushed the Enemy Territory engine to the limit and boasts some excellent game play. It's as realistic as you can make ET. It's development runs stagnant for long periods of time, but it is getting worked on. 

We need an open source battlefield like game based on ioquake3. :)
How can the graphics in Urban Terror be dated if you're then advocating ET and True Combat? They all run using the same engine! Heck, I think UT has better graphics than ET, even the weapon animations are smoother.

:confused:

Then again, I'm a Urban Terror master who'd rip you to shreads in a match, so no surprise you need to find some way to put down my 2nd-fav Linux game.

Just kidding! :)

(or am I?)

---

### Post by cmat on 2007-07-13
There are a few graphical issues which were fixed in the revised Quake 3 engine used in ET. One thing I noticed that people float above terrain made from patches (that awesome desert level). Not to mention no shadow is casted. May just be map bugs and not the programming and artwork itself.

---

