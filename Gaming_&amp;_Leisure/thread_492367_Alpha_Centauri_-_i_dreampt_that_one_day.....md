---
title: "Alpha Centauri - i dreampt that one day...."
date: 2007-07-04
forum: Gaming &amp; Leisure
---

### Post by Doctoxic on 2007-07-04
..... some kind soul made a single .deb file that :

* fully patches a bare install of the native SMAC pack
* adds in the extra (old) libs etc
* creates shortcuts for me that work


only i have tried all the guides/websites and still can't get the damned game to work - i'll settle for an idiots, step by step guide as a lot of the stuff i have seen assumes a fair amount of linux knowledge - as i am a  convert from windows i don't have it,  so need things explained VERY clearly  :D



zzzzzzzzzzzzzzzzzzzzzzzzzzz
am i awake yet?


doc

---

### Post by rettichschnidi on 2009-08-05
For the archive: We made somthing like this: [http://liflg.org/?catid=7](http://liflg.org/?catid=7)

Only thing you have to do on your own is to disable the Composite Extensions.

Feedback appreciated.

---

### Post by Ericj1186 on 2009-08-05
Nice link.  I will have to try this one: [http://liflg.org/?catid=6&gameid=81](http://liflg.org/?catid=6&gameid=81)

I loved AVP, but when I first played it, I would have nightmares from playing as the Alien and having people scream for their lives.

Any chance of an AVP2, with expansion, installer?

---

### Post by ELD on 2009-08-05
> **Ericj1186 said:**
> Nice link.  I will have to try this one: [http://liflg.org/?catid=6&gameid=81](http://liflg.org/?catid=6&gameid=81)

I loved AVP, but when I first played it, I would have nightmares from playing as the Alien and having people scream for their lives.

Any chance of an AVP2, with expansion, installer?

AVP2 was never ported as far as i know :(, shame, good game.

---

### Post by handy on 2009-08-08
I love the AC game.

I've run it years ago under windows & it would run fine for some time & then for no reason crash.  It did this enough times that I sadly gave up playing it.

Since then I've tried it multiple times; followed how-to's & installed it on more than one type of Linux distro.  I got the same experience, it would play for a while then for no obvious reason crash.

The last time I tried it was on OS X 10.5, someone had made it compatible for the Mac, so I went through the routine yet again, with the same results, play for a while then crash.

I will never attempt to install & play AC again. :(

---

### Post by peyre on 2009-09-02
I got it to run on my Xubuntu 9.04 machine recently.  The trick--for me at least--was I had to install it under my home folder; it just wouldn't work if I installed it to the default /usr/local.  Here are the instructions I wrote up for myself for future reference:


Install the game to somewhere in your home directory (don't let it install to the default, /usr/local/games/smac).  I installed it to /home/leon/Games/smac.  Install the whole game, of course.

Exit when setup is complete.

Patch the program by running smac-6.0b-x86.run.

Open loki_compat_libs-1.1.tar.bz2 and unzip the Loki_Compat to the Alpha Centauri folder.

You'll have to give the system extra information.  (Replace /home/leon/Games/smac with the path to the Alpha Centauri folder).  Use the following to open:

ALPHA CENTAURI
LD_PRELOAD=/home/leon/Games/smac/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib/libX11.so /home/leon/Games/smac/smac.dynamic

ALIEN CROSSFIRE
LD_PRELOAD=/home/leon/Games/smac/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib/libX11.so /home/leon/Games/smac/smacx.dynamic

TO CREATE ICONS

Create script files, e.g. runsmac and runsmacx, in the Alpha Centauri directory, containing (respectively) just the code above.

Make them executable (open a terminal window there and enter "chmod +x runsmac" and then "chmod +x runsmacx").

Create Launchers that point to those scripts.

---

### Post by rettichschnidi on 2009-09-03
Have you tried [http://liflg.org/?catid=7](http://liflg.org/?catid=7) ? Should be easier..

---

