---
title: "unreal tournament goty maverick 64"
date: 2011-05-12
forum: Gaming &amp; Leisure
---

### Post by casebomber on 2011-05-12
Has anyone been able to get ut99 working in maverick 64? Is it possible?

Got it to install and run with libgtk advice from post 2 at [http://ubuntuforums.org/showthread.php?t=1468422](http://ubuntuforums.org/showthread.php?t=1468422) but I still have no sound. Anyone know how to get the sound to work?

All rightey then it seems adding padsp before ./playut allows sound!

Now to figure out how to get the game to play at a reasonable speed...

all done!

using the info from [http://fingel.com/ut/howtos/utonlinux.html](http://fingel.com/ut/howtos/utonlinux.html) adjusting some typos and using padsp in the script instead of aoss the game works!

now, dropping my cpu to 1.6ghz (intel i5-2500k) the game seems to work flawlessly so far!

and by doing

gedit /usr/bin/ut

then adding
cd /home/yourname/ut
./playut

and saving I am able to run the ut command from anywhere to start

tried updating the ut version to 451b but my ut menu still says 4.36...

downloaded a linux version of the patch, ran checkfiles.sh and now running 4.51 baby! yeah!

---

### Post by HolgerB on 2011-05-12
u99 is well know for having issues with multiple CPU cores. It is best to assign it fixed to one core.

Have a look here in the old thread over at arch:
[https://bbs.archlinux.org/viewtopic.php?id=105280](https://bbs.archlinux.org/viewtopic.php?id=105280)

---

### Post by casebomber on 2011-05-12
wohoo my first ever reply on ubuntuforume!!! thanks! I was beginning to think I was being shunned for being such a noob.

It seems this person is using wine to run ut, can this relate to a native install?

---

### Post by HolgerB on 2011-05-12
> **casebomber said:**
> wohoo my first ever reply on ubuntuforume!!! thanks! I was beginning to think I was being shunned for being such a noob.

It seems this person is using wine to run ut, can this relate to a native install?
The issues occurs both under WINE as well as under native Linux. 

Usually noobs are only ignored in the more "experienced" Linux bb's (e.g. arch, gentoo). ;)

Simply re-assign the UT process to a certain core and see if this helps.
VSync should also be enabled. 

Beside CPU assignment sometime disabling any CPU throttle mechanisms also might help.

YMMV...

---

### Post by R33D3M33R on 2011-05-12
Please read this wiki entry: [https://help.ubuntu.com/community/Games/Native/UnrealTournament](https://help.ubuntu.com/community/Games/Native/UnrealTournament)

btw: you don't need 451b as this is a server only patch.

---

### Post by casebomber on 2011-05-12
Oof! that wiki does cover most of it. I got hung up at the first part as ./ did not work and sh did for the loki installer, so i guess i kinda drifted off after that...

great to know about 451b as I have been out of the loop for years

---

