---
title: "Games for my laptop?"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by ahaslam on 2006-06-13
Hi,

I'm interested in having a playable game on laptop. The machine is capable of playing most games that are a couple of years old. For example when I ran windows, I played GTA-VC and RTCW, along with older games such as QII and UT.

I've seen many native games in the repos, I would like some suggestions about any freely available games that you think may work on my system. I like most action/adventure games.

I've tried QII and UT under Wine and only UT worked (but the display wasn't centralised).
I also tried a Linux demo of Postal 2, but this crashed my system upon starting. Many games such as Tuxracer also crash my laptop, I guess that it's the state of the Via drivers for my Unichrome graphics. BTW glxinfo does show that dri is on. 

Any advice about the crashes would also be appreciated, maybe someone out there can play decent games using Via drivers?

Cheers,
Tony.

---

### Post by IYY on 2006-06-13
Post the specs of your laptop.

By the way, I don't think QII and UT need wine, there should be native versions for Linux (well, I don't know about UT, maybe only UT2004 is ported, but I'm sure I played QII on Linux).

---

### Post by ahaslam on 2006-06-13
[QUOTE=IYY]Post the specs of your laptop.

By the way, I don't think QII and UT need wine, there should be native versions for Linux (well, I don't know about UT, maybe only UT2004 is ported, but I'm sure I played QII on Linux).[/QUOTE]
I know that there's a naitive version of QII, I just don't own a copy. I want to try some free games, so I don't loose anything if it turns out to crash my system.

Cheers,
Tony.

---

### Post by seth0x2b on 2006-06-13
Try "Nexuiz" ( [http://www.alientrap.org/nexuiz/index.php]("http://www.alientrap.org/nexuiz/index.php") ). It's built on an optimised version of the Quake 1  engine so it should work just fine.

Also, here's a very good list of native running games(most of wich are GPL): 
[http://doc.gwos.org/index.php/Native_Games]("http://doc.gwos.org/index.php/Native_Games")


Cheers

---

### Post by eqisow on 2006-06-13
If you have the WIndows version of QII and Unreal tournament you should be able to install them (for free) using the Linux game engines. I'm no expert on this though, so try doing some Google searches. :)

---

### Post by seth0x2b on 2006-06-13
Don't know about UT, but Quake 2 uses the same game data, just the executable needs to be replaced.Just copy the windows instalation if you have it installed somewhere, or get the data from the original cd, then get the installer here [http://www.liflg.org/?catid=6&gameid=55](http://www.liflg.org/?catid=6&gameid=55)
I see you mentioned that you don't own a copy of Q2. Quake 2 is not free, so you will need a copy of the original game.Only the native version is free(the native version of the executable, NOT the game).

Cheers

---

### Post by ahaslam on 2006-06-13
[QUOTE=seth0x2b]Try "Nexuiz" ( [http://www.alientrap.org/nexuiz/index.php]("http://www.alientrap.org/nexuiz/index.php") ). It's built on an optimised version of the Quake 1  engine so it should work just fine.

Also, here's a very good list of native running games(most of wich are GPL): 
[http://doc.gwos.org/index.php/Native_Games]("http://doc.gwos.org/index.php/Native_Games")


Cheers[/QUOTE]
Woh, looks good. I'm downloading it now, I'll let you know if it works.;)

---

### Post by ahaslam on 2006-06-13
[QUOTE=seth0x2b]Don't know about UT, but Quake 2 uses the same game data, just the executable needs to be replaced.Just copy the windows instalation if you have it installed somewhere, or get the data from the original cd, then get the installer here [http://www.liflg.org/?catid=6&gameid=55](http://www.liflg.org/?catid=6&gameid=55)
I see you mentioned that you don't own a copy of Q2. Quake 2 is not free, so you will need a copy of the original game.Only the native version is free(the native version of the executable, NOT the game).

Cheers[/QUOTE]
I wasn't too clear. I did own a windows version, but I now only have the a backup of the install directory. Should your advice work with this?

...nexuiz has downloaded, I'm going to try it now.

---

### Post by seth0x2b on 2006-06-13
If you have the installed game, it's gonna work. Just get the Linux installer and install it in the Quake directory.It should work with no problem, as long as you have opengl setup ok.

---

### Post by ahaslam on 2006-06-13
Nexuiz looks great, and it doesn't crash my system. 
It's soo slow though, I even set it to 800x600x16 and turned off all the options. That made no difference at all, any ideas?

I'll try QII now.

---

### Post by ahaslam on 2006-06-13
[QUOTE=seth0x2b]If you have the installed game, it's gonna work. Just get the Linux installer and install it in the Quake directory.It should work with no problem, as long as you have opengl setup ok.[/QUOTE]
I can't figure out how to install the installer. 
As my previous attempt with wine was on Breezy, I installed it on Dapper. Clicking on the QUAKE2.EXE only brought up an error message saying that the file could not read (this didn't happen in breezy, it tried to load it). I then pulled up a terminal an changed to the Quake directory and typed 'wine QUAKE2.EXE' (well, wine Q, and then tab) hit enter and it works perfectly. I mean full screen, full resolution, high quality textures, using OpenGL.:D 

I just have a few questions:
1. how can I make a launcher for this, so that I don't have to use the terminal each time?
3. This backup directory of mine also has the two mission packs applied (I never completed either of these, so I'd really like to play them). They were set up to work with shortcuts to the Q2 exe, with a small addition so that the mission pack was loaded. How can I get them to work?
2. How can I play online?

---

### Post by seth0x2b on 2006-06-13
You don't have to use wine to run Quake 2.The installer gives you an Linux executable that you can run as is, without the use of wine.This will "seriously" increase the game's performance.
To use the installer, simply download it, fire up a terminal, go to the folder where you have downloaded the installer, and issue
```
sh <installer_name>
``` 
If you still decide to use wine to run Q2, just right click on desktop > Create launcher
type "Quake 2" in the "Name" field, and ```
sh -c "cd <quake directory> && wine quake2.exe "
``` in the "Command" field.
I'm not sure how you can use the mission packs.

Cheers

[EDIT] I found this huge quake 2 on Linux tutorial. It's really good reading and it has a mission pack installation section.
[http://webpages.onvoy.com/bobz/howto/Quake-HOWTO-3.html]("http://webpages.onvoy.com/bobz/howto/Quake-HOWTO-3.html")

---

### Post by ahaslam on 2006-06-13
Your command for the installer worked and the installation was successful. Although the new 'quake2.sh' file does not work. Running with wine still works, but that launcher doesn't work for me, can you double check it?

Any thoughts about online play?

It's weird how Nexuiz didn't work, as it's based on Q1. Do you (or any body else) have any ideas to get it working? - It looks great!

Thanks for the advice,
Tony

PS> what's the 'sh' &  '-c' mean, what do they do?
I've just watched the trailer for Nexuiz, I really want it to work properly now! - They've really put some elbow grease into pollishing the Quake engine!

[EDIT] The tutorial that you linked to was a great help with the mission packs, they work perfectly.
Thanks again,
Tony.

---

### Post by ahaslam on 2006-06-13
[QUOTE=seth0x2b] type "Quake 2" in the "Name" field, and ```
sh -c "cd <quake directory> && wine quake2.exe "
``` in the "Command" field.[/QUOTE]
It does work. It just didn't like my directory name, "Quake II". I renamed the directory to "Quake2", made it the same in the launcher and everything's OK. I've now setup different launchers for each of the mission packs. :) 

I guess that the install didn't work because of the latest patch being applied already, along with the mission packs.:-k 

Any further help with Nexuiz would be appreciated. ;) 

Thanks again,
Tony.

---

### Post by seth0x2b on 2006-06-14
[quote=Anthony Haslam]
PS> what's the 'sh' &  '-c' mean, what do they do?
[/quote] 
"sh -c" executes the standard linux shell (sh) with the command that comes after "-c", in out case: "cd <quake directory> && wine quake2.exe"

"cd <quake directory>": changes directory to the quake directory.If you wouldn't do this, then wine would not be able to find the Quake executable, because it will try to run in from whatever your current working directory is.
"&&" tells the shell to execute the next command after executing the previous one. You have to do this if you want to issue 2 different commands in one line.
"wine quake2.exe": self explanatory :)
I have to go to the university now, but I'll have a look at Nexuiz later.I know it's based on the Quake 1 engine, but it's seriously modified, so it won't work as smooth as Quake 1

Cheers

---

### Post by charlieg on 2006-06-14
Check my list here, with tons of Free games most of which will run fine on your laptop:
[http://freegamer.blogspot.com/](http://freegamer.blogspot.com/)

---

### Post by ahaslam on 2006-06-14
[QUOTE=charlieg]Check my list here, with tons of Free games most of which will run fine on your laptop:
[http://freegamer.blogspot.com/](http://freegamer.blogspot.com/)[/QUOTE]
Nice site, I see that Nexuiz 2 is out today. ;) 
Still the same speed though... sloooow (I'll look into diffreent graphics drivers).

---

### Post by The Cosmic Hobo on 2006-06-14
[QUOTE=charlieg][http://freegamer.blogspot.com/](http://freegamer.blogspot.com/)[/QUOTE]
Wow... that's a lot more games than I thought were out there for Linux!
Although to be fair, I'm now cursing being a laptop owner. I think I'll have to build myself a new desktop PC, just so I can play Nexuiz or some of those other nifty-looking games on the front page (especially the space sims)!

---

### Post by ahaslam on 2006-06-14
[QUOTE=Anthony Haslam]As my previous attempt with wine was on Breezy, I installed it on Dapper. Clicking on the QUAKE2.EXE only brought up an error message saying that the file could not read (this didn't happen in breezy, it tried to load it). I then pulled up a terminal an changed to the Quake directory and typed 'wine QUAKE2.EXE' (well, wine Q, and then tab) hit enter and it works perfectly. I mean full screen, full resolution, high quality textures, using OpenGL.:D [/QUOTE]
Not as perfect as I thaught. I can run 'timedemo1' and get 25fps, I can go through the first level with no probs, but it crashes near the end of the second level :mad: 

I've also tried 'openarena' and 'tremulous' (tremulous is a great game) Unfortunatly they both crash and freeze the system at random points :( 

I think that I'll give up on 3d games untill there's some decent Via drivers. I've just tried the openchrome version and it just didn't work for me. I've heard that the Via driver in X.org 7.1 has been updated, I hope an update is issued for Dapper and not have to wait for the next Ubuntu.

Tony
:(

---

