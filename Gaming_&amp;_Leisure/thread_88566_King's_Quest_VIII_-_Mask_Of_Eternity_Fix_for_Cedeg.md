---
title: "King's Quest VIII - Mask Of Eternity Fix for Cedega/Wine"
date: 2005-11-10
forum: Gaming &amp; Leisure
---

### Post by blueturtl on 2005-11-10
Now I know a lot of King's Quest fans hate Mask of Eternity, but I thought it was a fun game when it got out, and it had some innovations that I would have like to have seen in more adventure games! Now, I'd been trying to get the game to work under Cedega for some time. After 5.0 was released I was still getting the same error every time I tried to boot the game after install. I began to suspect the problem had actually to do with playing back the intro video rather than running the game itself, so I looked and looked and finally found a solution, so here it is! This should also work under older versions and vanilla WINE.

[LIST]
[*]After installation, edit the file /Sierra/Mask/main.kq with whatever text editor
[*]Find where it says *aviPlayed=0* and change it to *aviPlayed=1*
[*]Save the file and boot the game!
[/LIST]

Additional hints:
[LIST]
[*]Do not click on the intro movie item in the game main menu. ;)
[*]Do not attempt to switch to Direct3D rendering, this will cause the game to crash.
[/LIST]

For those who don't know, King's Quest 8 tried to mix arcade action, puzzle solving and 3D with some role playing elements (experience gathering, health, weapon and armor stats etc). The combination is something new. You get and adventure game, where you can go anywhere you like (no more set paths). A lot of old-style adventure fans dislike the added combat, and 3d worlds but I thought it was awesome. The puzzles are still a vital part of the game, and most of the time you will be scratching your head on how to proceed. Unfortunately the game didn't do well enough to warrant another sequel, which is why there is fan-project going on for KQ9. To my disappointment though, the project aims for one of those old-school adventure games and merely resorts to expanding the beauty of the game.

---

