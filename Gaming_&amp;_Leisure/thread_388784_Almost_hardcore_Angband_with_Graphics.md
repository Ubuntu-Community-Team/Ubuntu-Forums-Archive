---
title: "Almost hardcore: Angband with Graphics"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by EvilMarshmallow on 2007-03-19
Ok, so I've been playing **[Angband]("http://www.thangorodrim.net")** now for about 10 years.  I started off hard-core but somewhere along the way I got lazy and switched to the graphical tileset in Windows.

Now that I've made the switch to Ubuntu, I can't figure out how to get graphical tiles to work.  According to the help files I should run the executable with -g... but this doesn't work.  I have seen screenshots on linux forums using graphical tiles, so I know this is possible.  The Angband website even has a .rpm package that's supposed to install the graphics options... but I'll be darned if I can get it to work.  I installed alien, and the package converted and installed flawlessly... but still no pictures.

Any other Ubuntu users out there still playing Angband?

---

### Post by cjl2301 on 2007-04-01
I'm trying the same thing and I got this far:

1) Download the tiles from [ftp://ftp.sunet.se/pub/games/Angband/Extra/angband-graf.zip](ftp://ftp.sunet.se/pub/games/Angband/Extra/angband-graf.zip).

2) Go to /var/games/angband/xtra and mkdir a directory called 'graf'

3) Unzip angband-graf.zip into /var/games/angband/xtra/graf.

The -g option will then work.


Now, I'm trying to figure out how these items:

A) How do I change to "bigtile" mode?
B) How do I change the font?
C) How do I select the 32x32 tiles?

I could do all these from the main menu in the windows version.

---

### Post by EvilMarshmallow on 2007-04-01
Thanks for the tip on the regular tiles... that got me started, and now I found another forum with the answer we're looking for (at least, it's what I wanted... :) )
[B]
_[Have a look at this thread]("http://www.oesf.org/forums/index.php?showtopic=22353&pid=153903&st=30&#entry153903")[/B]_

I tried it on mine, with the 32x32 tiles in the folder you said to create... and it's working.

---

### Post by cjl2301 on 2007-04-01
YES!  Thanks that was exactly what I was looking for also.  Works great now.

---

