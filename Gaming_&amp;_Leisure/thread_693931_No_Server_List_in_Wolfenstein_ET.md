---
title: "No Server List in Wolfenstein: ET"
date: 2008-02-11
forum: Gaming &amp; Leisure
---

### Post by galvao on 2008-02-11
Greetings. Just installed Wolfenstein: Enemy Territory (v. 2.60). Everything seems to work fine, except for the servers list... It just doesn't fetch any server..

Can anyone please help?

TIA,

---

### Post by Dogfighter on 2008-02-11
the in game browser is crap. :)
apt-get install xqf

;)

---

### Post by galvao on 2008-02-11
Thanks for trying, but:

1 - This is so not true: Played this game for years on Windows and never ever had any problems and
2 - Doesn't solve my problem...

Anyone else could please help?

TIA,

---

### Post by c/Kr3t on 2008-02-11
have you set permissions correctly?

use all of these commands

sudo chmod 777 -R /path/to/ET/
sudo chown -R your_username ~/.etwolf/
and
sudo apt-get install libgtk1.2

---

### Post by galvao on 2008-02-11
The only command from that list I didn't ran before was:
sudo chmod 777 -R /usr/local/games/enemy-territory

Done it, but the problem remains...

Any other ideas?

---

### Post by c/Kr3t on 2008-02-11
it has to be sudo chmod 777 -R /usr/local/games/enemy-territory/et.x86

---

### Post by galvao on 2008-02-11
Since I did with the "-R" flag one level above it shouldn't be necessary, but did it as you've said anyway, still no success... This is so bizarre... Can it be something with Punk Buster?

Any other ideas?

TIA,

---

### Post by c/Kr3t on 2008-02-11
well the .x86 was a guess to be honest, when i originaly did it i sent it to the .xpm image but as you said, the -R flag would have taken care of it anyway....i'm thinking it would be punkbuster, either that or becuase you're useing the 2.6 patch. mines just regular 2.55

[http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408](http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408)

that's the page where i downloaded mine from, on it there are some PB commands to put into the in game console that deals with PB

hope it helps

---

