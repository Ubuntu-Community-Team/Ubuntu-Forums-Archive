---
title: "How do I uninstall Enemy Territory???"
date: 2007-07-05
forum: Gaming &amp; Leisure
---

### Post by AndyCat on 2007-07-05
Hi there. I installed the game and havent been able to play, first because I have no sound, second because every time I try to join a server nothing happens and the game close automatically. 
FInally I decided to uninstall it. The Big question is how do I do that????

Im a noob here and I have no idea how to do it.....


Thanks in advance for the help


Ps... Any other game I can play????

---

### Post by NeoLithium on 2007-07-05
Hmmm, well, depending on your config, Enemy territory might have problems. However the way that it's installed, you can just install your enemy-territory directory
```
sudo rm -rf /usr/local/games/enemy-territory
```
Then remove the custom user directory
```
rm -rf /home/YOUR_USERNAME/.etwolf
```

---

