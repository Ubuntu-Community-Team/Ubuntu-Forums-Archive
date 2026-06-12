---
title: "Problem with Quake 4 (1.4.2)"
date: 2008-01-04
forum: Gaming &amp; Leisure
---

### Post by CyberMoon on 2008-01-04
Hello, first excuse me for my poor english (i speak spanish)

I have ubuntu 7.10 AMD64 and I download the Binary of Quake 4 (version 1.4.2) and I installed, next I copy the pk4 files necesary to start the game and the game start normally... but when I choose single player campaing and it is loading.... when the progress bar is for the middle the game return to the main menu (without sound) and the terminal catch this error:

------------ Processing events --------------
---------------------------------------------
**Error ERP_DROP: entityDef not found: player_viewweapon**
TODO: Sys_SetClipboardData
------------ Game Map Shutdown --------------
---------------------------------------------
********************
**ERROR: entityDef not found: player_viewweapon**
********************
------------ Game Map Shutdown --------------
---------------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
Shutting down SDL subsystem
--------------- Game Shutdown ---------------
rvStatAllocator:  dump of usage stats
        32 total bytes handed out in 2 requests
        begin game:      1;  end game:        0
        player hit:      0;  player kill:     0
        player death:    0;
        damage dealt:    0;  damage taken:    0
        stat team:       0
        flag capture:    0;
        flag drop:       0;  flag return:     0
------------ Game Map Shutdown --------------
---------------------------------------------
Shutdown event system
---------------------------------------------
shutdown terminal support

The pk4 are not corrupted... so I dont have Idea of what happened.

My PC:
Intel D965 GCC
Core 2 Duo 4300 @ 1800Mhz
1 Gb RAM
Gefore  7600 GS 256 Mb.

Help Please

---

### Post by Vamp898 on 2008-01-04
First upgrade to Ubuntu 7.10

than this

[http://www.holarse-linuxgaming.de/h2006/space/Quake+4](http://www.holarse-linuxgaming.de/h2006/space/Quake+4)

---

### Post by Sockerdrickan on 2008-01-04
Quake 4 works wonderfully with 7.04 and why would you even say Upgrade to 7.10 when said > I have ubuntu 7.10 AMD64 

---

### Post by Vamp898 on 2008-01-04
i could bet there was 7.04 some minutes ago

---

### Post by CyberMoon on 2008-01-04
How I said, The game start normally but when I start the single player the progress bar fills to the middle then the game return to the main menu losing the sound.

I repeat, THIS is the error:
---------------------------------------------
Error ERP_DROP: entityDef not found: player_viewweapon
TODO: Sys_SetClipboardData

But... I dunno how fix it!

---

### Post by BreathEasy on 2008-01-04
OK, it's probably best you start from scratch and follow these instructions: [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

It's particularly important you have the necessary PK4 files on that list, plus the md5 hash values must match exactly what you have.

---

### Post by CyberMoon on 2008-01-04
> **BreathEasy said:**
> OK, it's probably best you start from scratch and follow these instructions: [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

It's particularly important you have the necessary PK4 files on that list, plus the md5 hash values must match exactly what you have.

This is that I have when use the md5 command:

> ** a9f6a2e4bf8e193591954f75d1d39f85   game000.pk4**
1ddd9d4067679d4ffdbf0cd6dd9695f5   game100.pk4
e74002463f81728cf3072c92b867dc41   game200.pk4
[B]b201b914167f47061fa5f975af527122   pak001.pk4
dabe2c88e004198947431250e3f4ca1d   pak002.pk4
8573f05af4c9568880cc464d06292079   pak003.pk4
12ff4006a7f7181ac16835d05c59905f   pak004.pk4
3576213f4e00f06baf3cd5de089a538a   pak005.pk4
aec7bb418b9a86256f9e5daee894dee2   pak006.pk4
0f53b4fb4df2c14fcd10012baf8b2f87   pak007.pk4
b099d75869f0ffcbcb8e5166374af345   pak008.pk4
cb2b44bf573559dc19b488d9e1e5bec3   pak009.pk4
d024073349dc917b4feab49e6abc417b   pak010.pk4
98c854d94ce1da5272952b77821823df   pak011.pk4
e77a2fda6656495d38773e05bbffda33   pak012.pk4[/B]
c1383eeb82a7d303b27d3884180ffd22   pak013.pk4
e2ec0b8ce4c460bf196ef61280ae20e0   pak014.pk4
3f005b0703c7b8f7c77627d2f091dd9e   pak016.pk4
15af0fb2c33b0743edc0ff11199fffb0   pak018.pk4
5865f9172801fee0c48b7a83d17b29ca   pak019.pk4
615306b72e71f2ed9224b3f16183795c   pak021.pk4
79d90c4564d043036b0e3831d158ea7d   q4cmp_pak001.pk4
609d085ed8bbd8db1e3b52a06818a745   zpak_english_01.pk4
a4d6207c12ce47f1effc60d7fe8b5b9d   zpak_english_02.pk4
9d13ed76b9db99175381a83b6d46a929   zpak_english_03.pk4
1dffc34ee05313f790ceea670a744e11   zpak_english_04.pk4
**669d6d9a30b798d19434972475b98c53   zpak_english.pk4**
2cabddd692e214c78c20a464da43f1ef   zpak_french.pk4
4ee7eb637cde6bcfe3a9ffac5e4579dd   zpak_italian.pk4
36eee38e6c2dce12986f7192a5a996e5   zpak_spanish.pk4


and this is from Quake 4 Page:

>  a9f6a2e4bf8e193591954f75d1d39f85  game000.pk4
b201b914167f47061fa5f975af527122  pak001.pk4
dabe2c88e004198947431250e3f4ca1d  pak002.pk4
8573f05af4c9568880cc464d06292079  pak003.pk4
12ff4006a7f7181ac16835d05c59905f  pak004.pk4
3576213f4e00f06baf3cd5de089a538a  pak005.pk4
aec7bb418b9a86256f9e5daee894dee2  pak006.pk4
0f53b4fb4df2c14fcd10012baf8b2f87  pak007.pk4
b099d75869f0ffcbcb8e5166374af345  pak008.pk4
cb2b44bf573559dc19b488d9e1e5bec3  pak009.pk4
d024073349dc917b4feab49e6abc417b  pak010.pk4
98c854d94ce1da5272952b77821823df  pak011.pk4
e77a2fda6656495d38773e05bbffda33  pak012.pk4
669d6d9a30b798d19434972475b98c53  zpak_english.pk4
2cabddd692e214c78c20a464da43f1ef  zpak_french.pk4
4ee7eb637cde6bcfe3a9ffac5e4579dd  zpak_italian.pk4
36eee38e6c2dce12986f7192a5a996e5  zpak_spanish.pk4

They are identical!! so I dont understand what is the problem.

---

### Post by CyberMoon on 2008-01-06
any idea?

---

### Post by rajeev1204 on 2008-01-07
U probably tried it already but still... 

have u tried reinstalling?

Also change ownership of .quake4 folder in home directory(hidden folder)

chown -R <USERNAME>:.quake4


Might help.

---

### Post by nicolasito on 2008-01-26
i have the same problem on my kubuntu 7.10 it shows the loadbar filling and when it ends im back into main menu and the same message appears on console.

made my user into the "game" group, and also tested the fix proposed here, nothing worked. also md5um was ok.
still no clue... :(

tryed changing sound from alsa to oss, to see if it was some sound problem (it was lost in the moment of failure), but the same problem.


**NOW got it fixed**, not the best one but still works. Made the install in ~/ and worked good, here are the steps i did:

1- mount the q4 CD
2- created quake4 and quake4/q4base directories in my home dir.
3- copied all packs from the CD to the q4base dir.
4- runned the install as my user and installed in my home dir.


i dont like this solution since i had to install it for my 2 brother's user also.... so it takes up 9GB++ to get the game for the 3 of us, ln -s gave me the problem of view_weapon also.

ohh btw  quake version is 1.4.2, and sabot is kicking head all the time ^_^

---

### Post by CyberMoon on 2008-01-30
with the 1.3.2 versión the game runs fine!!

---

### Post by dakhath on 2009-02-13
I have the same issue... unfortunately I'm running Slackware 12.1, so I don't know just how much help can be lended.  Here's some details:

[LIST=1][*]I torrented the quake4-linux-1.4.2.x86.run file from zerowing.idsoftware.com.[*]The checksums for my data files off the CD are in order.[*]The game is installed to /usr/local/games/quake4/.  This directory is 777 root/root.[*]I'm running as a user and the links to the binaries are installed in my home directory.[*]The install went without a hitch.[*]The game boots into the opening videos just fine.[*]I changed my settings to increase the graphics and keyboard settings, and they have been kept.[*]I tried going into the multiplayer.  The game browser was reading data fields incorrectly: game names were reading as #str0712 and the like.[*]Every time I tried to load a network game, it said I needed more data to download... for a regular deathmatch game.[*]I sat and waited about 30 minutes for additional code to be downloaded.  Eventually the download broke and stopped about 2/3s of the way through on every download[*]I said "forget it" and tried to play a single-player game.[*]It got halfway through the loading screen for the first level, bailed to the main menu and the sound stopped working.[*]I checked zerowing.idsoftware.com for information, restarted the game as "quake4 +set developer 1 + set logfile 1".[*]The first error I could recognize that looked like it was around the time of the crash was: "Error ERP_DROP: entityDef not found: player_viewweapon".[*]After this it said "TODO: Sys_SetClipboardData" and shut down both the game map and the sound system.[*]I've tried running it from a menu item I created, from the shell in my home directory and from the shell in the /usr/local/games/quake4 directory.[*]I even tried chmodding 777 all the pk4 files in q4base.[/LIST]

More info concerning my system environment:
[LIST][*]Slackware 12.1 Linux 2.6.24-5.smp kernel[*]KDE 3.5.9[*]gcc 4.2.3[*]bash 3.1.17(2)[*]AMD Athlon64 3000+ (2.0GHz)[*]1GB RAM[*]nVidia GeForce 7800GT[/LIST]

---

### Post by caravel on 2009-04-15
> **dakhath said:**
> "Error ERP_DROP: entityDef not found: player_viewweapon"

I'm having the same problem, running 8.10 64bit with fglrx driver installed and working.  Funnily enough I have Doom3 and UT2K4 working perfectly it's just Quake4 that I cannot get to run properly.  All the Paks are fine, in fact I've copied them from the CD several times.  I've also set the permissions correctly and I've even tried installing the whole thing as a user in my /home/user directory.  Whatever I do, I still get that same error after trying to start a single player campaign.  The game loads up, sound is working and I can configure the graphics etc but it just jumps back to the main menu after the loading bar goes half way.

I've also been googling this for the last few days and still found no solution.  All of the solutions offered are for different issues.

I may go back to 32 bit as I had it running perfectly under 32 bit in the past.  Unless there are some missing libs that need to be installed?

Any help gratefully appreciated.

---

### Post by rizzeh on 2009-04-15
runs perfect here on Mint6 x32, using quake4-smp executable

---

### Post by caravel on 2009-04-15
Yes I've tried running from the quake4 and quake4-smp and it has the same result.  I think I'll have to go back to Ubuntu 32 bit.

:(

---

### Post by caravel on 2009-04-16
I've formatted, reinstalled 32 bit Ubuntu and reinstalled Quake4 1,4,2 again and still the same problem.  I've changed the ownership of /usr/local/games/quake4 to my user and tried again, still no good.  I've just no idea why this isn't working...

Any ideas?

---

### Post by gotthardt on 2009-04-19
I was having some strange problems with Q4 on 8.10 until I set /system/prefernces/appearance->visual effects to none.

---

### Post by caravel on 2009-04-21
Yes, I have compiz disabled.

Anyway I've managed to solve it.  The error is caused by a very simple mistake.  The installer has 3 options: To install the game, "select game version" and install punkbuster.  I unchecked the last two, whereas I *should* have unchecked only the last one (there is no need to uncheck thee last one, but I don't intend to play online) hit enter then selected "install all but the German version".  It's as simple as that...

I was then faced with a working game with ugly low res textures.  After some furious googling and testing I found that you need to make a few changes to the ~/.quake4/q4base/Quake4Config.cfg

```
seta com_videoRam "512"
seta sys_videoRam "512"

seta image_downSizeLimit "1024"
seta image_ignoreHighQuality "1"
seta image_downSizeBumpLimit "128"
seta image_downSizeSpecularLimit "1024"
seta image_downSizeBump "1"
seta image_downSizeSpecular "1"
seta image_downSize "1"
```

My graphics card has 512MB so for a 256MB card it would be "256" instead of the "512".

---

