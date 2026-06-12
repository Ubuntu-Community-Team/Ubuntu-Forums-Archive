---
title: "UT2004 failed to fully write..."
date: 2006-04-16
forum: Gaming &amp; Leisure
---

### Post by sinfreealex on 2006-04-16
I have tried to run the installer off of the DVD and  these are my results: 

> myname@mydomain:/media/cdrom0$ sudo sh linux-installer.sh
Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2004 for GNU/Linux 3186......................................................................
Can't create /home/sinfreealex/ut2004: File exists
UZ2: Failed to fully write [/home/sinfreealex/ut2004/Textures/ArboreaTerrain.utx]!
./setup.sh: line 148: 10113 Aborted                 "$setup" "$@"
myname@mydomain:/media/cdrom0$ sudo sh linux-installer.sh
Password:
Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2004 for GNU/Linux 3186......................................................................
UZ2: Failed to fully write [/usr/local/games/ut2004/Textures/ArenaTex.utx]!
./setup.sh: line 148: 10338 Aborted                 "$setup" "$@"


What am I missing here?](*,)   I figured that UT2004 would be the easiest game I have to install.  I  still remember the great feeling I got years ago when I sucessfully installed the original UT on my old system.  Any help is appreciated.

Have a good one.

---

### Post by mscman on 2006-04-16
It looks to me like there might already be files in the path the installer wants to use, and it won't overwrite them.  I would make sure that the directory /home/sinfreealex/ut2004/  doesn't contain anything, or better yet: delete the whole thing.  Then try running it again.  I may be wrong in thinking this, but that's what I gather from the error messages you're getting.

---

### Post by Perfect Storm on 2006-04-16
Also if you install at your /home you don't need to sudo it, only if you want it to install at /usr/share/games/ut2004 just make sure you don't start the game afterwards when you have sudo permission. If you do you have to **sudo chown -R <username>:<username> /home/<username>/.ut2004/**

Also I've heard from [handy]("http://ubuntuforums.org/member.php?u=55341") that there can be problem running the install script from the CD/DVD. A copy of the install script to your desktop and run it from there.

---

### Post by sinfreealex on 2006-04-16
Thanks.  Copying the install script to my Desktop worked.

[QUOTE=Artificial Intelligence]Also if you install at your /home you don't need to sudo it, only if you want it to install at /usr/share/games/ut2004 just make sure you don't start the game afterwards when you have sudo permission. If you do you have to **sudo chown -R <username>:<username> /home/<username>/.ut2004/**

Also I've heard from [handy]("http://ubuntuforums.org/member.php?u=55341") that there can be problem running the install script from the CD/DVD. A copy of the install 
script to your desktop and run it from there.[/QUOTE]

---

### Post by fredrik20 on 2008-02-21
Thank you.
This was the answer to the problem!

/Fredrik20

---

### Post by pradhishkumar on 2010-05-31
hello ppl.  i m having similar problem. having the dvd installation medium which has folders for cd1 cd2 .....   installer starts fine and then encounters error saying

could not fully write to tautnxxxxx.tfg 

setup encountered an error in x86 and quits

i check the installation folder and found onli 280 mb has been written. i could not understand  please advise



update
:

i have checked that the file its trying to write is on cd2 folder in the dvd medium and ut fails when trying to copy that file.

---

