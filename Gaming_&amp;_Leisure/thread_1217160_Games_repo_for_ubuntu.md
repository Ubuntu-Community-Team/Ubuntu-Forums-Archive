---
title: "Games repo for ubuntu"
date: 2009-07-19
forum: Gaming &amp; Leisure
---

### Post by Shea7993 on 2009-07-19
So asof recently ive went over to ubuntu 9.04 and i like lol, problem is im a gamer, and ubuntu doesnt have much =[ only game i realy play is frets on fire \m/ awsumness, but love my shooters, and was forced to do a dualboot with windows just to play majority of games on windows, seeing as not alot of games have opengl support and is useless for wine lol, but seriously, ive come accross some sites that supply native linux clients for some games, however im not too sure how to compile and install these things (im a newb) so im wondering, isnt there a repo that contains these games and native linux clients aswell as other great multiplayer and singleplayer mods? eg: Americas Army, DOOM stuff, Quake stuff, Heretic and Hexen stuff and others?

---

### Post by tommcd on 2009-07-19
Here is the official  gaming site for Ubuntu:
[http://gwos.org/doku.php](http://gwos.org/doku.php)
There are many online FPS games available for Ubuntu / Linux. Nexuiz, Sauerbraten, Urban Terror, and World of Padman are some of the best and most popular.
Also, if you have the retail Windows versions, you can install Doom3, Quake 4, and Prey to run natively in Linux without wine. Yo can get the linux installers for Doom3 and Quake4 here:
[ftp://ftp.idsoftware.com/idstuff/](ftp://ftp.idsoftware.com/idstuff/)
The info for Prey is here:
[http://icculus.org/prey/](http://icculus.org/prey/)
Write back if you have any questions about installing those.
Linux Game Publishing ports games for linux:
[http://www.linuxgamepublishing.com/](http://www.linuxgamepublishing.com/)
I also dual boot with Windows XP, mainly so I can install a Windows game if and when I want to. I just had to play *FEAR 2 Project Origin*. I just love Alma!!

---

### Post by Shea7993 on 2009-07-19
thanx, and yes i know bout installing DOOM3, Q4 and prey natively, got the retail versions, except that i have to download  the linux clients which is a problem due to small cap size, however it couldnt hurt to add these to a repository and just go to add remove to get it =]

I checked the links you provided and its usefull thanx, but 1 thing i have to ask, ive got a few apps and games, but their not debians, they are .run or targz, how do i go about to install those?

ps. do you know any good and usefull repositories for ubuntu?

---

### Post by Grishka on 2009-07-19
> **Shea7993 said:**
> thanx, and yes i know bout installing DOOM3, Q4 and prey natively, got the retail versions, except that i have to download  the linux clients which is a problem due to small cap size, however it couldnt hurt to add these to a repository and just go to add remove to get it =]

I checked the links you provided and its usefull thanx, but 1 thing i have to ask, ive got a few apps and games, but their not debians, they are .run or targz, how do i go about to install those?

ps. do you know any good and usefull repositories for ubuntu?

start .run files from the terminal, they're usually installers. tar.gz files are simply archives, like .zip or .rar, you just unpack them and see what's inside. usually you'll find the program source inside, these have to be compiled by yourself. there are many useful repos for ubuntu, but no single, big, all-inclusive one. official ubuntu repos have the biggest software collection. but see [getdeb](http://www.getdeb.net/) for some convenient game installers, though it's not a repo, their .debs have to be downloaded manually. also, people keep some nice stuff in their PPAs on Launchpad. search [here](https://launchpad.net/ubuntu/+ppas).

---

### Post by tommcd on 2009-07-19
> **Shea7993 said:**
> ... ive got a few apps and games, but their not debians, they are .run or targz, how do i go about to install those?

Programs that are provided in a "program.run" file are binary packages that you can run like this:
```
./program.run
```
or:
```
sh program.run
```
This will install or run the program in your home directory. This is usually fine. To install the program system wide so that all users of the system can have access to it, run the package with sudo. Usually, you will get a choice of where to install it if you run it with sudo. A good place for games is /usr/local/games. It is fine to run it in your home directory without sudo though.

A program.tar.gz or program.tar.bz is a source code package that can be unpacked like this:
```
tar -vxzf program.tar.gz
```
or:
```
tar -xvjf program.tar.bz
```
Usually there will be a README or INSTALL file inside the directory that is created after you unpack it. Read those for specific instructions on how to install it.

Programs provided in as .run or .tar.gz packages may have dependencies that you would need to install. Usually you can find those in the Ubuntu repos.
It is usually best to search for a .deb version of the program first though, before you try to compile it from source code.

---

### Post by joeelmex on 2009-07-19
I'm a gamer and that was the main reason I have not moved from the windows os. I have been windows free from my main pc for a month now.  I got all my favorite windows games running in cedga. I play left 4 dead, crysis, world of Warcraft, half life games, and grid defence.  I am having a blast and enjoying gaming Linux.

---

