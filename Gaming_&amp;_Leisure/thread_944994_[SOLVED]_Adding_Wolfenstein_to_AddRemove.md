---
title: "[SOLVED] Adding Wolfenstein to Add/Remove"
date: 2008-10-11
forum: Gaming &amp; Leisure
---

### Post by Georgia boy on 2008-10-11
Hi. It's probably a dumb question but will the Wolfenstein  games be added to the Ubuntu games or the Open Source section of the games? I can remember playing on the old dos game. I know, showing my age on that one. :)  It was fun then. Would be nice if we could have it available just to go to the Add/Remove and do a quick install from there. Would be a lot less hassel and maybe fewer headaches for some people. I know, dumb question butis it an open source game or not or is it just a "free" game? 
Also is it still available to be played as a single person instead of multiple play?

Thanks

Tom

---

### Post by MaxIBoy on 2008-10-12
The game engines for all the Wolfenstein games are open source. The levels, textures, sounds, models, and sprites are still copyrighted, however. In other words, putting them in the repositories without permission would be an act of piracy.

ID Software would probably give permission to put the shareware/freeware/demo versions in the repositories, but in general there's a taboo on copyrighted content of any kind. 

Wolfenstein: 3d, the Nocturnal Missions, Spear of Destiny, and Return to Castle Wolfenstien are all still available from ID Software's store, and thus available for single player.

---

### Post by mikedep333 on 2008-10-12
You can install freedoom from the repos. It is a free rewrite of the original doom, which was the sequel to wolf 3d.

---

### Post by Georgia boy on 2008-10-12
Sorry. I didn't know that there were parts of the game that was still copyrighted. So much for that idea. But thanks for the responses. Guess I'll give the freedoom one a shot then. I agree about not putting copyrighted stuff for downloading. There's enough problems with what's been going on with the music business as it is without bringing that kind of headache into the Ubuntu repositories. Sorry about the question. Didn't know all of the facts on it.

Went to the repositories. Couldn't find the "freedoom" game. Guess it got taken off for some reason or is it called something else?

Thanks
Tom

---

### Post by MaxIBoy on 2008-10-12
Try this in the terminal:
```
sudo apt-get install freedoom
```

By the way, I could scarcely believe my eyes when I saw this:
```
apmaxtothemax@maxtothemax-laptop:~$ apt-cache search doom
doom-package - Installer for Doom data files
doom-wad-shareware - Shareware game files for the 3D game DOOM
dosemu - The Linux DOS Emulator
deutex - composition tool for doom-style WAD files
freedoom - free game files for the 3D game DOOM
glbsp - nodes builder for Doom-style games; has support for OpenGL
kdoomsday - countdown timer panel applet for KDE
libglbsp-dev - node builder library for OpenGL-based Doom-style games (headers)
libglbsp2 - node builder library for OpenGL-based Doom-style games
overkill - bloody 2D action deathmatch-like game in ascii-art
prboom - clone of the legendary first person shooter Doom
slashem - A variant of Nethack
slashem-gtk - A variant of Nethack (Gtk window port)
slashem-sdl - A variant of Nethack (SDL window port)
slashem-x11 - A variant of Nethack (X11 window port)
tilda - terminal emulator with first person shooter console likeness
unmass - Extract game archive files
maxtothemax@maxtothemax-laptop:~$ 

```
Note the package "doom-wad-shareware."


I think that ought to be taken out of the repositories.

---

### Post by Georgia boy on 2008-10-12
Maxiboy, you're saying that the "freedom" shouldn't be in the repositories either right? Maybe that's why I couldn't find it. Looks like it had been removed before then. Maybe someone noticed the same thing you did and had it removed. Well, guess I'll just keep looking for some game that has action but can also be a single player game that is in the repositories. Don't want to get involved in teams when I don't understand the game. Well everyone I sure do appreciate the advice that has been given. Have a wonderful weekend for what's left of it.
Thanks again
Tom

---

### Post by MaxIBoy on 2008-10-12
> **Georgia boy said:**
> Maxiboy, you're saying that the "freedom" shouldn't be in the repositories either right? Maybe that's why I couldn't find it. Looks like it had been removed before then. Maybe someone noticed the same thing you did and had it removed. Well, guess I'll just keep looking for some game that has action but can also be a single player game that is in the repositories. Don't want to get involved in teams when I don't understand the game. Well everyone I sure do appreciate the advice that has been given. Have a wonderful weekend for what's left of it.
Thanks again
Tom

No, freedoom **should** be in the repos.

Doom-wad-shareware should not. Damn the special permissions, that's still copyrighted content.

---

### Post by Georgia boy on 2008-10-13
Got a question on the doom-wad- shareware part. Is this all part of the installation package of "Freedoom" game? Or, is this something else? If it is part of the "Freedoom" game package then I guess I'll just bypass it all together. Got any ideas of some good stand alone action packed games that's available on the repos? It could also be a team player but I would want to be able to play alone until I understand the game and get the feel for it. Then when confidence in the game is there I could venture out and join teams. But I want to learn it first. I was trying one out yesterday and had someone wanting to join me when I had just got started. Guess I was in the wrong section somehow unless it is a team only game and I installed by accident. it was the "Battle for Wesnoth" game. I was trying to learn it when that happened. I closed out of the game and decided to remove due to not finding how to play as a stand alone until I learned the game. So, you can see that I'm not the type who's able to just jump right into a game and start playing. Any and all ideas will be appreciated.

Thanks in advance for all advice

Tom

---

### Post by MaxIBoy on 2008-10-13
Freedoom isn't a full game, it's just an updated version of the game engine. The idea behind freedoom is, if you have a copy of the original doom, you can copy over some files and then you won't need an emulator to run it. Or, you could just get the shareware files (doom-wad-shareware) and then you'll be able to run the free demo without an emulator.

Also, there are entire, free games which use the doom engine, you'll be able to run those with freedoom too. "Total conversion" mods where absolutely no content is leftover from the original game will also run.




But I see you're looking for other games.

Alien Arena is in the repos. However, the version in the repos is consistently out of date. To get a recent version, stop by [red.planetarena.org](red.planetarena.org). To get an even more recent version (and we're talking new versions every week) follow the instructions that I wrote here:
[http://corent.proboards42.com/index.cgi?board=bugreport&action=display&thread=3252&page=1#32179](http://corent.proboards42.com/index.cgi?board=bugreport&action=display&thread=3252&page=1#32179)


Alien Arena is playable in singleplayer (and can be a lot of fun in singleplayer,) but once you move onto multiplayer you'll see the light.

---

### Post by Georgia boy on 2008-10-13
Sorry for the confusion. I was misunderstanding about the "freedoom". I was thinking that it was a game. I'll have to try and get the Alien Arena. Have you tried the Open Arena that's in the repos? I was debating about downloading it. Can't remember if it can be played as a stand alone or not. I had gone to the site listed in the description but seems as though the individual removed the latest version due to some compromise with the codes or something. Think that someone had added soomething that they shouldn't have. He mentioned that when he does release the latest version that everyone will enjoy it. What do you think? Is the one in the repos also a stand alone and is it any good? I really like the action packed ones. I can remember the fun that the Wolfenstein dos demos were playing. Had thought about downloading the ET but seems as though it looked like a team game only. Such is life. :)

Thanks 
Tom

---

### Post by MaxIBoy on 2008-10-13
Wolf: ET is indeed team-only (and multiplayer-only,) but fun nonetheless.

A good one to try is Urban Terror. Don't get the linux installer, because it doesn't work. Run the Windows installer under WINE, and the Linux version will actually come with it. (And the Mac version.) I don't think it's in the repos. Just Google for it.

OpenArena is okay, but it's not the best out there. However, unless you have a small hard drive, there's no reason not to get it.

---

### Post by Georgia boy on 2008-10-13
I'll have to give the open arena a whirl. Maybe even check out the Urban Terror. I'll have to ge the Wine set up. I've been reading through out the forum about all kinds of games. Seems like some great ones are here for Linux. Going to have to get them and try them out. Thanks for all of the advice given. I'm constantly learning. As you can see I haven't been on Linux very long so I have a lot of dumb questions. I try to find answers by researching forum for similar problems then when I can't find one I ask. The people in this forum have all been a great help. A very friendly bunch. 
Again thanks for all of your help.
Tom

---

