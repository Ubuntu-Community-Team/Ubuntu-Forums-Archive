---
title: "Hitman games"
date: 2007-10-09
forum: Gaming &amp; Leisure
---

### Post by Tellisk on 2007-10-09
Today I bought Hitman, Hitman 2 and Hitman Contracts. It was a bundle for like 30 bucks and seemed like a good deal. I figured I'd check Wine's AppDB when I got home, and return it if it didn't look doable.

After a little reading, it seemed the games were good to go. Gold ratings by several members with the newer versions of WINE.

I have installed the first and second games, each unplayable for different reasons. The first game brings up a SecuROM error ( [http://securom.com/message.asp?m=module&c=7000](http://securom.com/message.asp?m=module&c=7000) or [http://securom.com/message.asp?m=module&c=8008](http://securom.com/message.asp?m=module&c=8008) , depending on which version of Windows I set in winecfg).

I have tried a few cracks people have made for SecuROM, but they haven't helped at all.

The second game pops an error message:
> Hitman 2 does not have the required access to its installation directory. Please make sure you have write permissions to C:\Prog~FBU\EIDO~\HITM~R5B

(Path not found)

With buttons labeled "Abort," "Retry," or "Ignore." When I hit "Ignore," the game seems to try to start, but pops up a Fatal error:

> OpenGL: Unable to switch to fullscreen. Try changing the resolution, refresh rate or the color depth.

and closes when I click "Ok." I tried turning it off of fullscreen mode in the Config.exe file, but my settings there don't seem to be saved (when I open it again, the fullscreen box is checked on.)

Does anyone have any insight about what else I can try?

---

### Post by cogadh on 2007-10-09
Well, I've never tried to run Hitman and Hitman: Contracts barely worked but screws up on the cutscenes (ruins the story). Hitman 2, however, runs like a dream.

First off, you must use a cracked exe to run it, the copy protection on the game is not supported in Wine (yet). You also need to manually set the default renderer in the game to OpenGL instead of Direct3D:
[LIST=1]
[*]Open a terminal and go to Hitman 2's directory: ~/.wine/drive_c/Program Files/Eidos Interactive/Hitman 2 Silent Assassin
[*]Enter this: 
```
wine notepad Hitman2.ini
```
NOTE: This is one situation where it is best not to use a Linux native text editor.
[*]Look for the line "DrawDll RenderD3D.dll" and change it to "DrawDll RenderOpenGL.dll"
[*]Save the file
[/LIST]
When you run the game, make sure you launch it from the terminal and cd to the game's install directory first:
```
cd ~/.wine/drive_c/Program\ Files/Eidos\ Interactive/Hitman\ 2\ Silent\ Assassin/
wine hitman2.exe
```
If the game's performance is still not great or it crashes, try changing Wine's default DirectDraw renderer to OpenGL, see the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page for details on that.

---

### Post by Tellisk on 2007-10-09
I had already changed the Hitman.ini file as you mentioned. Can you tell me which cracked .exe worked for you?

Thanks.

---

### Post by cogadh on 2007-10-09
I'm pretty sure I got it from GameCopyWorld (can't verfiy, site seems to be down right now), but I'm sure you can find it any number of places. I don't think it really matters which one you use, they all do the same thing. Just make sure you get a replacement hitman2.exe that matches your version of the game.

---

### Post by Tellisk on 2007-10-09
Hmm. Okay, I thought I had tried one of those (from GameCopyWorld), but I will try again.

---

