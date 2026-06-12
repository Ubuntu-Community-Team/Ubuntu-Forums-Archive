---
title: "world of warcraft,Lucid studio and wine"
date: 2010-05-05
forum: Gaming &amp; Leisure
---

### Post by nick_geetar on 2010-05-05
First I would have to said Lucid is amazing. I just installed it on my gateway but anyways. I'm a musician slash wowhead and I am trying to play wow with wine. It loads up and I'm able to play,but it takes a while to load up and I have to turn the graphics all the way down in order to play. When I had windows installed on this machine it ran wow great at about the mid range graphics setting sitting about 32 fps but in lucid running with wine I'm on the lowest graphics setting running at only 10 fps. Just wandering if it is my graphics driver or what. I have a intel mobile chipset 4. The main problem i'm having is it's like the it's tearing or rendering something wrong i don't know but i'll attach some screen shots in game. Any help would be much appreciated.

---

### Post by darkforester67 on 2010-05-05
Its becouse your running a game that uses a program called Direct X that is built only for windows, what wine does its like it translates the programs language into one the computer can read.

In other words any directX games aren't built for linux computers
Windows: DirectX
Linux: OpenGL

---

### Post by NicMagic on 2010-05-05
Hi

As darkforester67 said, DirectX is not available in linux (Ubuntu) and you have to use OpenGL, which is arguably better...

if you go here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18555]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18555")
you will find that WoW is tried and tested with Wine + Ubuntu. It will require some tweaks which can be found by following the thread but runs quite well...

I personally have the same settings for WoW in Ubuntu as I do in my Windows XP load barr the death animation (under video settings)

Good luck

---

### Post by nick_geetar on 2010-05-05
I didn't really find anything on there that helped me. Although i'm a complete linux noob. I tried putting the -opengl but i don't think it did anything. Still just sitting at bad frame rate unable to play. Am I doomed or did i miss something crucial.

---

