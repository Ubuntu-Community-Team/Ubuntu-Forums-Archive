---
title: "How do i install RTCW?"
date: 2005-10-03
forum: Gaming &amp; Leisure
---

### Post by Sheytan on 2005-10-03
I can't find any how to for this game.

I got Quake 3 working with this guide [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=30](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=30)

---

### Post by Hairy_Palms on 2005-10-03
u just install it by typing ./et-2.60.sh or whatever the filename is

---

### Post by Sheytan on 2005-10-03
Thanks for the reply but i followed this guide and got it to work :)

[http://zerowing.idsoftware.com/linux/wolf/INSTALL](http://zerowing.idsoftware.com/linux/wolf/INSTALL)

---

### Post by Hairy_Palms on 2005-10-03
ahhh i thought u meant enemy territory, my mistake :)

---

### Post by fakie_flip on 2006-11-06
> **Sheytan said:**
> Thanks for the reply but i followed this guide and got it to work :)

[http://zerowing.idsoftware.com/linux/wolf/INSTALL](http://zerowing.idsoftware.com/linux/wolf/INSTALL)

How is it playing in Linux? I'm thinking of getting it.

---

### Post by kr0n1x on 2006-12-26
> **fakie_flip said:**
> How is it playing in Linux? I'm thinking of getting it.

RTCW is dead (the multiplayer part)...is an old game....


you can fine more players in Wolfenstein Enemy Territory...is free (search it on google) and not too old like RTCW

---

### Post by jagwah on 2006-12-26
While RTCW multiplayer may well be dead, the singleplayer is a lot of fun, it'll keep you busy for a while. The game itself runs fine in Linux. So if you want it for SP, and don't mind that MP is practically non existent, go for it, it'll be very cheap now days as well.

---

### Post by fakie_flip on 2006-12-29
I have all these files for enemy territory.

et-linux-2.60-update.x86.run
et-linux-2.60.x86.run
Enemy Territory 2.60b (extracted folder from et2.60blinux.zip)
et2.60blinux.zip

I thought et-linux-2.60.x86.run was the game and et-linux-2.60-update.x86.run was a patch. Now I have an extra file et2.60blinux.zip. Maybe it is a newer patch, but it's files look like the game. Why do I have two files that look like the game? Maybe one file is for patching et and the other file is for patching the dedicated server. Can anyone confirm this? What is each one file and what is it for? How can I correct the error below?

```
[chris@localhost Enemy Territory 2.60b]$ ls
EULA_Wolfenstein_Enemy_Territory.txt  linux  macosx  README.txt  win32
[chris@localhost Enemy Territory 2.60b]$ cat README.txt 
CVE-2006-2082: directory traversal / information leak in Quake III Arena auto download feature

Ludwig Nussel and Thilo Shulz discovered a vulnerability letting a malicious client download files from a server if auto download is enabled ( sv_allowDownload 1 ).

Issue #2 ( CVE pending ): R_RemapShaders buffer overflow

A second issue fixed in this release would let a malicious server exploit a buffer overflow to execute a shellcode on connecting clients.

--
Updated binaries for the following games are available:

Quake III Arena - fixed at version 1.32c
Return To Castle Wolfenstein - fixed at version 1.41b
Wolfenstein: Enemy Territory - fixed at version 2.60b

If you run a server with any older version, please upgrade or consider turning off autodownload ( set sv_allowDownload to 0 ). Wolfenstein: Enemy Territory servers http/ftp download feature is not affected by CVE-2006-2082. If you don't wish to upgrade, you can decide to only enable http/ftp downloads and disable legacy downloads in that particular case.

Finally, server administrators should note that game servers should be running in restricted environments as much as possible ( unpriviledged accounts and chroot jails ). It's a good thing to do the same for clients, or at least ensure that you are properly firewalled.

[chris@localhost Enemy Territory 2.60b]$ ls
EULA_Wolfenstein_Enemy_Territory.txt  linux  macosx  README.txt  win32
[chris@localhost Enemy Territory 2.60b]$ cd linux/
[chris@localhost linux]$ ls
etded.x86  et.x86
[chris@localhost linux]$ ./et.x86 
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/chris/.etwolf/etmain
/BACKUP/Applications/downloads/Enemy Territory 2.60b/linux/etmain

----------------------
0 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg - I am missing essential files - verify your installation?
[chris@localhost linux]$ 
```

---

### Post by kr0n1x on 2006-12-29
read this (ita): [http://kronixcb.blogspot.com/2006/12/aggiornare-wolfenstein-enemy-territory.html](http://kronixcb.blogspot.com/2006/12/aggiornare-wolfenstein-enemy-territory.html)

is my blog with the complete guide to update correctly the game...


now i try to translate in short form XD

1. install et-linux-2.60.x86.run
2. install et-linux-2.60-update.x86.run
3. extract 2.60b patch and overwrite older files (2 files et and etded)

next of this, continue to read in my blog how to install etpro 3.2.6 mod:) is impossible to play without it! 

bye

---

### Post by fakie_flip on 2007-01-22
> **kr0n1x said:**
> read this (ita): [http://kronixcb.blogspot.com/2006/12/aggiornare-wolfenstein-enemy-territory.html](http://kronixcb.blogspot.com/2006/12/aggiornare-wolfenstein-enemy-territory.html)

is my blog with the complete guide to update correctly the game...


now i try to translate in short form XD

1. install et-linux-2.60.x86.run
2. install et-linux-2.60-update.x86.run
3. extract 2.60b patch and overwrite older files (2 files et and etded)

next of this, continue to read in my blog how to install etpro 3.2.6 mod:) is impossible to play without it! 

bye

Why install the update? Do you even know what you are doing and what it is for? I read this from a website.

About Wolfenstein: Enemy Territory - Linux 2.60 PatchThis update for the Linux version of Wolfenstein: Enemy Territory patches v2.56 to 2.60.

If you have version 2.60 of the game, you do not need to update it. If you have an older version than 2.60 of the game, then you should install the update. Why did you tell me to do that?

---

### Post by kr0n1x on 2007-01-23
> **fakie_flip said:**
> Why install the update? Do you even know what you are doing and what it is for? I read this from a website.

About Wolfenstein: Enemy Territory - Linux 2.60 PatchThis update for the Linux version of Wolfenstein: Enemy Territory patches v2.56 to 2.60.

If you have version 2.60 of the game, you do not need to update it. If you have an older version than 2.60 of the game, then you should install the update. Why did you tell me to do that?

the website u readed is old..or fake.

i play et, not only in public, but also in PCW like ESL, clanbase, and other...then i know that 2.60b is the correct patch to play in most server...

all the server with <=2.60 patch aren't updated good..

install 2.60b :)

more info? read this: [http://www.clanbase.com/rules.php?lid=984#chap_5](http://www.clanbase.com/rules.php?lid=984#chap_5)
are the rules to play european ladder of ET...(official competition)

also in public, now all publics (or the 98% :P ) are updated to 2.60b and NEEDS 2.60b (client side) to play..because the mod ETPRO 3.2.6 NEED 2.60b patch;)

sorry for my bad english, bye

---

### Post by fakie_flip on 2007-01-28
> **kr0n1x said:**
> the website u readed is old..or fake.

i play et, not only in public, but also in PCW like ESL, clanbase, and other...then i know that 2.60b is the correct patch to play in most server...

all the server with <=2.60 patch aren't updated good..

install 2.60b :)

more info? read this: [http://www.clanbase.com/rules.php?lid=984#chap_5](http://www.clanbase.com/rules.php?lid=984#chap_5)
are the rules to play european ladder of ET...(official competition)

also in public, now all publics (or the 98% :P ) are updated to 2.60b and NEEDS 2.60b (client side) to play..because the mod ETPRO 3.2.6 NEED 2.60b patch;)

sorry for my bad english, bye

I don't think you understand my question. You said in your directions to install the 2.60 patch and the 2.60b patch. How can you know which patches are needed? Should all patches be installed or only the newest patch or only patches with patch versions newer than your game version?

I have another question for some others. I am trying to get another Wolfenstein game to work, the single player game Return to the Castle Wolfenstein. From the picture,

[http://chris1.hopto.org/~chris/wolfmp.png](http://chris1.hopto.org/~chris/wolfmp.png)

You can see it is having many problems. I went to the options menu and text began overlapping other text. Then I could not click apply or go out, so I had to switch to a console (ctrl alt f1) and kill the game and then fix my resolution. I have several files. These files are all confusing because there is so many of them and no directions I have found tells what each is for, so I am unable to determine which one I need. Sense I can not find any uninstallers for either Wolfenstein games (ET or RTCW), I had to manually remove the directory /usr/local/games/wolfenstein. If anyone knows about a way to properly uninstall either of the games through a program or script, please tell me. What are each one of these files below and what are they for? Does anyone know without guessing? I have the RTCW CD, but it does not include everything needed for the game to work in Linux. I have copied the pak files from a Windows installation that I need for the game to work in Linux. If I didn't, the game would not have ran at all. It is not clear what each file is for, why there is so many, what each one does, and how to determine which ones are needed.

```
chris@ubuntu:~$ ls
wolf-linux-1.41-3.x86.run
wolf-linux-1.41b.x86.run
wolf-linux-1.4-full.x86.run 
wolf-linux-GOTY-maps.x86.run
wolf-linux-update-1.41.x86.run
```

---

### Post by kr0n1x on 2007-01-28
if you have the version 2.60 of ET, install the 2.60b patch

if you have 2.56, install first 2.60, and next the 2.60b

have i reply correctly to your question? i hope yes...or i can't understand good english:( sorry

---

### Post by fakie_flip on 2007-01-28
> **kr0n1x said:**
> if you have the version 2.60 of ET, install the 2.60b patch

if you have 2.56, install first 2.60, and next the 2.60b

have i reply correctly to your question? i hope yes...or i can't understand good english:( sorry

I understand now. Thank you. I only need to install the 2.60 patch version if my game version is older than 2.60. My game version is 2.60, and earlier I installed the 2.60 patch and 2.60b patch, and the game ET is working fine, but RTCW is not. You can see from the picture it is having many problems, and now I am confused by even more files. It has many more files. Do you know about that game?

---

### Post by kr0n1x on 2007-01-29
mmm...i'm not sure oh this...but i try to help you:

install the game (by the cd)
then, install the full version of 1.41b patch: [http://www.3dgamers.com/dlselect/games/returnwolfenstein/wolf-linux-1.41b-full.x86.run.html](http://www.3dgamers.com/dlselect/games/returnwolfenstein/wolf-linux-1.41b-full.x86.run.html)

and now install OSP mod...(the most popular...used in pcw) last version is 0.9 i think...

now you can play (i hope...)

try:) bye

---

