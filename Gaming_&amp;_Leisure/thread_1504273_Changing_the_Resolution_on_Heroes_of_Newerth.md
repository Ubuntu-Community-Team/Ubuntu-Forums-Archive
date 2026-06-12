---
title: "Changing the Resolution on Heroes of Newerth"
date: 2010-06-07
forum: Gaming &amp; Leisure
---

### Post by BlackRat90 on 2010-06-07
I accidentally changed my game Resolution up to an unsupported res.
Now i cant get into the game to change it back because my monitor just goes black every time I run the game. 

Ive tried everything, reinstalling, looking through the files for some kind of config, but nothing so far. Im sorta new to games on linux so perhaps Im just not looking right but there must be some way to change the res without entering the game?

---

### Post by BlackRat90 on 2010-06-07
What really stumps me is reinstalling doesn't fix it...shouldn't it delete the old configuration and replace it withe the default?

---

### Post by Cresho on 2010-06-07
#rm "~/.Heroes of Newerth/"

do that in terminal without the pound sign

---

### Post by BlackRat90 on 2010-06-07
I fixed it...
I found the config file here:

/home/nate/.Heroes of Newerth/game/startup.cfg

I was able to fix the problem there

---

### Post by Psyket on 2011-06-25
Got the same problem now, but I cant find any "startup.cfg" in the map?

---

