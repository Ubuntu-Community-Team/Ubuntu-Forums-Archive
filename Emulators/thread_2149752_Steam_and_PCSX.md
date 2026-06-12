---
title: "Steam and PCSX"
date: 2013-05-29
forum: Emulators
---

### Post by DoubleYouSee23 on 2013-05-29
I am having a bit of difficulty getting my emulated games to play through steam. 
I really like the idea of using Big Picture Mode and my controller to browse through my collection of old school games, as is presented here [http://pinkpoodlewoof.tumblr.com/post/27968826596/adding-emulator-games-to-your-steam-library](http://pinkpoodlewoof.tumblr.com/post/27968826596/adding-emulator-games-to-your-steam-library) as well as various other places online. I jut can't seem to find linux instructions for pcsx. Any help would be appreciated.
From all the instructions i have read the "Start in" setting is to be left alone, in the "target" setting i have tried
"/usr/games/pcsx" -cdfile  "~/Desktop/castlevania/castlevania.iso"
"/usr/games/pcsx" -cdfile  ~/Desktop/castlevania/castlevania.iso
/usr/games/pcsx" -loadiso  ~/Desktop/castlevania/castlevania.iso
and many other variants i have come across online (if you can't tell, I'm not even 100% of the commands or the formatting...)
Any help?

---

### Post by deadflowr on 2013-05-29
I launch pcsx games throught the terminal with just 'pcsx --option(like cdfile, or whatever) path to game'.
And it's probably /usr/bin/pcsx, rather than /usr/games/pcsx.

---

### Post by DoubleYouSee23 on 2013-05-29
So, I tried running PCSX from the terminal earlier, trying to figure out the correct commands to use in steam...
"pcsx --cdfile ~/Desktop/castlevania/castlevania.iso" and
"pcsx --cdfile /Desktop/castlevania/castlevania.iso" and
pcsx --cdfile Desktop/castlevania/castlevania.iso" But none work, 
what's the command you're using deadflowr?
and thanks.

---

### Post by deadflowr on 2013-05-29
I copied my .desktop file for pscx in /usr/share/applications to my home folders .local/share/applications folder so I could add my entries to the quicklist on Unity.

for the cd player and games that won't rip
```
pcsx -runcd -nogui
```

and then for my ripped games
```
pcsx -nogui -cdfile file
```
When I ripped them I don't remember what they were (ISO or otherwise), but I think all I needed was the .bin file inside.
so my paths are all to a .bin file.

Look in 
```
man pcsx
```
For other options as well.

---

### Post by DoubleYouSee23 on 2013-05-30
So ive got it running in windowed mode through steam, but only one game per emulator can be loaded....
 If anyone is interested;
1.click the 'add game' button in the loewr left hand corner of steam
2. add a non steam game
3.select your emulator from the list provided
4. your emulator should show up under games. Right click and select properties
5. change the title to the name of the game your going to be adding
6. under 'Target' add "-nogui -cdfile the name of the file" WITHOUT QUOTES, so the entire entry looks something like this
"/usr/games/pcsx" -nogui -cdfile ~/PSX/Castlevania/Castlevania.iso
first part with quotes, second part without.
7.click okay. If you use tile mode, or big picture mode, right click on your awesomely emulated game, select 'provide custom image' and provide your custom image that you probably got from here [http://steambanners.booru.org/](http://steambanners.booru.org/)
i'll repost if i figure out the full screen issue, or a workaround so i can have more than one game per emulator.

---

