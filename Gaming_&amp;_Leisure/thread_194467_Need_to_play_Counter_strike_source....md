---
title: "Need to play Counter strike source..."
date: 2006-06-11
forum: Gaming &amp; Leisure
---

### Post by Copernicus on 2006-06-11
CS:S is the only thing keeping me from being on ubuntu all the time, I need some detailed instructions on how to install steam, so I can play counterstrike source at any time just like in WIndows...

System specs:
athlon 64 3000+
1x 80gb sata
1x250gb sata
nvidia geforce 6800LE
1gb ram

running ubuntu 6.06 ONLY

cable 5mb down internet connection

Thanks for any help you can provide.

---

### Post by christhemonkey on 2006-06-11
From the wine website:

> NB: This is for all versions of Counter-Strike: Source, since all versions must be run through
Steam.

This game will work in current versions of wine if you:

1. Install the appropriate version of winetools from [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

2. Install Steam using winetools
**Note that using winetools will ensure that dependencies (currently) needed to run the game are correctly installed and configured**

3. Change the "steam" script winetools installed to run steam, to contain the
following:

#!/bin/bash
cd #/directory/containing/steam/*
WINEDEBUG="-all" nice -n 20 wine Steam.exe

(this should prevent the whitescreen crash and alleviate the in-game stuttering problem
somewhat)

Known issue with steam:

If when trying to start counter-strike: source steam throws an error and says its registry was
in use by another process, this seems due to a tendency of the steam client to crash when trying to shut down and release its registry.

You can fix this problem by shutting down steam cleanly (keep running and exiting steam itself until you get a clean shutdown
without any errors after "Shutting down" - watch the console you ran steam from) and then restarting it.

Once steam has been shut down cleanly and restarted the error should not occur.

Thoughts -

(i) Personally I'd tend to set things to directx 7 for the time being (go to Games Tab > right
click Counter-Strike: Source > Properties > Launch Options and add -dxlevel 70) - this
- it's not the prettiest way to play, but it seems to give the most playable framerates at the moment, and seems by far the most stable way to play.

(ii) In the past Steam updates have been followed by serious errors running CS:S (or even just
steam), including serious lockups. When running after an update, be sure that you're ready to
switch to another tty at the first sign of trouble - preferably having a "while true; do killall
wine-preloader;done" sitting ready in it just in case. Just a thought.

*In unix format, not windows format.

---

### Post by gripir-arch on 2006-12-21
Is this a error occured by wine or steam?

---

### Post by hikaricore on 2006-12-21
Alot of programs run perfectly in wine then crash while exiting, honestly there's no telling what's at fault, but more than likely at the moment I'd bet it's wine.  This is by no means a crippling issue, you just have to want to play badly enough to type a few lines before starting the game again.  Ohhh the effort.  Make a script for it if need be.  :P

---

