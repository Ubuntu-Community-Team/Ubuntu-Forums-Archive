---
title: "[WoW] WoW freezes when leaving the game"
date: 2007-04-09
forum: Gaming &amp; Leisure
---

### Post by Gunn3r on 2007-04-09
Hello to all.
Since last WoW patch (that i patched yesterday) that I'm having this issue.
The game loads well, I play well, no issues whatsoever but when I log out and click Exit The Game (on the login screen) the process freezes and stops responding. 
I have to KILL the process because WoW doesn't close no matter what I do or time I wait (even END the process doesn't do a thing).

I noticed this yesterday as I said, because I tried to patch and the BlizzardDownloader won't move an inch because the game was still running when Downloader popped up and while it downloaded the content. 
Had to KILL the game for the downloader to patch the game properly.

I'm using a Geforce 6600GT AGP (but never had any issues before) in a AMD 3000+ system with 1GB DDR400 and I already tried to load the previous version (0.9.33) but the end is the same... locks up when leaving the game. 
Driver version is the latest in 6.06 repos,  (using Dapper, of course :D ) WINE is 0.9.34 and it's set for Windows 2000 with everything as default.

Any similar problems with any of you, guys?

Thanks for the help

---

### Post by Sammi on 2007-04-09
Try upgrading to a newer video card driver than the one in the official Dapper repos. Dapper is getting a bit dated you know ;)

I personally like the Envy script very much for doing this and you can find a deb file and instructions right here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Use version 0.8.2 of the script not 0.9.1, because the newer one doesn't support Dapper and the old one is fine. It's from February this year and is up to date and stable.

Oh and you need to log out and do ctrl+alt+F1 to get to a clean command prompt where you can run it simply by writing "envy".

---

### Post by Gunn3r on 2007-04-09
I don't think the problem is with my video driver... as I said before, it didn't give me a headache until now. Even in the game, there are no graphical issues whatsoever, everything is smooth and polished.
The problem seems related to this... that WoW doesn't "tells" wine to shutdown the wineserver, so it's just hangs there waiting for something.

Yes, i know that dapper is getting old, but i like it better than Edgy and will format+set up the new Feisty soon, so it's not useful to use Envy now.

I'm sorry for the terms but i'm no programmer/linux geek, guru, whatsoever. just a random guy that likes Ubuntu beter than Windows.

---

### Post by justin whitaker on 2007-04-09
> **Gunn3r said:**
> I don't think the problem is with my video driver... as I said before, it didn't give me a headache until now. Even in the game, there are no graphical issues whatsoever, everything is smooth and polished.
The problem seems related to this... that WoW doesn't "tells" wine to shutdown the wineserver, so it's just hangs there waiting for something.

Yes, i know that dapper is getting old, but i like it better than Edgy and will format+set up the new Feisty soon, so it's not useful to use Envy now.

I'm sorry for the terms but i'm no programmer/linux geek, guru, whatsoever. just a random guy that likes Ubuntu beter than Windows.

Can you alt-tab out or alt-F2 and kill all wine processes?

BTW: I run WoW and TBC on Feisty via Crossover. I am one of the Linux is better than windows crowd too.

---

### Post by Gunn3r on 2007-04-09
Yes i can do that. I can CTRL+ALT+LEFT or RIGHT also to go to another desktop. the thing just doesn't closes down, the layer... so the game just continues to give me music (literally) until i KILL it.

It's not a big fuss, to KILL but... I just don't want to wreck the game, that's all. was just wondering if anyone was having this problem. and i thought this only happened in Windows world LOL... well was fun until now :) 

any ideas ?

PS.- Ok, I was playing a bit waiting for some more ideas and it seems that, if I choose Exit the Game directly within WoW (without logging out 1st) it logs out and leaves the game with no problem. so the problem is really in the EXIT command in the login screen not "saying" to Wine to close the layer...

---

