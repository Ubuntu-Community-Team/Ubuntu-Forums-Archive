---
title: "space games"
date: 2007-05-17
forum: Gaming &amp; Leisure
---

### Post by whitecore on 2007-05-17
can anyone tell me wear i can get some space games like vega strike and x2:the threat

---

### Post by hikaricore on 2007-05-17
You can find vegastrike in the ubuntu repos, though it might be in universe or multiverse repos ([repository info here]("http://help.ubuntu.com/community/Repositories/Ubuntu")), also at it's website here: [http://vegastrike.sourceforge.net/](http://vegastrike.sourceforge.net/)

But I highly recommend Battlestar Galactica - Beyond The Red Line: [http://www.game-warden.com/bsg/downloads.html](http://www.game-warden.com/bsg/downloads.html)

There's only a demo out now, but it's frackin amazing.  :)

X2 is a commercial game which can be purchased for Linux from Tux Games: [http://www.tuxgames.com/details.cgi?&referrer=linuxgames&gameref=131](http://www.tuxgames.com/details.cgi?&referrer=linuxgames&gameref=131) (demo download also at this link)
Also X3 is up for presale (estimated release May 2007): [http://www.tuxgames.com/details.cgi?&referrer=linuxgames&gameref=143](http://www.tuxgames.com/details.cgi?&referrer=linuxgames&gameref=143)

** Almost forgot to mention freespace2 which was open sourced.

You can find the data via one of sites listed here: [http://www.hard-light.net/forums/index.php/topic,38195.0.html](http://www.hard-light.net/forums/index.php/topic,38195.0.html)
Freespace linux installer (may not work as intended in all cases): [http://icculus.org/~ravage/freespace2/](http://icculus.org/~ravage/freespace2/)
And a wiki about extracting cd data, compiling/installing and configuring the game: [http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux](http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux)

---

### Post by whitecore on 2007-05-18
I was only using them as an example of the type of game play for others games out like them.
Thanks for ansering though

---

### Post by eilu on 2007-05-18
A good one is Astromenace, it's free for Linux users. [http://www.viewizard.com/astromenace/index_linux.php](http://www.viewizard.com/astromenace/index_linux.php)

---

### Post by charlieg on 2007-05-18
Two other good free ones:
- [Oolite]("http://oolite.aegidian.org/")
- [No Gravity]("http://www.realtech-vr.com/nogravity/")

Article on Free Gamer about space games:
[http://freegamer.blogspot.com/2006/06/open-source-3d-space-games.html](http://freegamer.blogspot.com/2006/06/open-source-3d-space-games.html)

---

### Post by sdowney717 on 2007-08-18
scott@scott-desktop:~$ ./BtRLDemoInstaller.run
Verifying archive integrity... All good.
Uncompressing Beyond the Red Line Demo.................................................................................................................
dirname: missing operand
Try `dirname --help' for more information.
cp: cannot stat `/data/players/single/Nugget.pl2': No such file or directory
Couldn't run Beyond the Red Line Demo (btrl_demo.bin). Is FSO_DATA_PATH set?



game installed ok and game wont start up.
Any ideas?

---

### Post by sdowney717 on 2007-08-18
sudo gave me less errors, so now what is FSO path?


scott@scott-desktop:~$ sudo ./BtRLDemoInstaller.run
Password:
Verifying archive integrity... All good.
Uncompressing Beyond the Red Line Demo.................................................................................................................
dirname: missing operand
Try `dirname --help' for more information.
Couldn't run Beyond the Red Line Demo (btrl_demo.bin). Is FSO_DATA_PATH set?
scott@scott-desktop:~$

---

### Post by sdowney717 on 2007-08-18
Ha, I went into where the game was installed and ran the bin directly and it works.

---

