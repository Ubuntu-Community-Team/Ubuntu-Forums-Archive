---
title: "Personally port games?"
date: 2009-07-12
forum: Gaming &amp; Leisure
---

### Post by wolfyking2 on 2009-07-12
I was wondering, if it's possible to personally port a game to linux, like World of Warcraft, LOTRO, Elder Scrolls, Need for Speed, Mabinogi heroes, etc etc, and be able to play online.  I'm not saying I know how to do this, I'm just asking.

---

### Post by Sigurd Suhm on 2009-07-12
Unfortunately this is not possible. Unless the creators released the source code for the game the only way is to run some sort of emulated environment in Linux (like Wine) to run programs for other platforms.

---

### Post by del_diablo on 2009-07-12
You can, but what is needed makes it impossible(about).
Basicaly you would have to:
*Make it compitable with all the previus file formats
*And scripts
*Compitable with the other clients
*Etc

Which are all closed, some cases where enough people already have dugged enogh to make it possible to go ahead(ex: DaggerXL, OpenMorrowind, other), its possible. But the work it takes? That is what makes it impossible.
But the worst part is the amount of time you use to figur out how the insides of the blackbox looks and works.

---

### Post by ruzkie on 2009-07-12
it's possible but maybe you won't be done before you die of old age. but who knows =)

---

### Post by Sigurd Suhm on 2009-07-12
Projects like DaggerXL and OpenMorrowind are not ports of the games. Those are simply remakes for another platform. Porting a game would mean taking the original game and make the source code cross platform. Since very few commercial games are open source this is not possible. Of course it is possible to make remakes of games. However since you seem to be interested in online play this brings up a great issue. Official servers would not accept a client from a copy of a game. You could set up your own server for a game but playing across the original version and the remake version would not be possible.

---

### Post by efikkan on 2009-07-12
> **wolfyking2 said:**
> I was wondering, if it's possible to personally port a game to linux, like World of Warcraft, LOTRO, Elder Scrolls, Need for Speed, Mabinogi heroes, etc etc, and be able to play online.  I'm not saying I know how to do this, I'm just asking. If an individual wants to do this, he/she would need to make a contract assisgning this individual to port the game to new platforms. Take a look [here]("http://www.phoronix.com/scan.php?page=article&item=linux_gaming_frank&num=1").

Games using OpenGL, and perhaps runs on Mac, would be rather simple to port to GNU/Linux, this includes all games from Blizzard. Games running on PS3 uses OpenGL ES.

Games using DirectX and other proprietary technologies needs replacements for these. Replacing Direct3D with OpenGL usually takes a skilled developer/team 3-6 months, depending on the size of the game. Most of the shaders can be converted quickly.

---

