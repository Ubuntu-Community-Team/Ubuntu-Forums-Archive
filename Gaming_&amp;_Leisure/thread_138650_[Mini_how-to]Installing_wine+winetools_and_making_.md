---
title: "[Mini how-to]Installing wine+winetools and making cs1.6 and even cs:s work!"
date: 2006-03-02
forum: Gaming &amp; Leisure
---

### Post by Zubzub on 2006-03-02
-Install the latest kernel from kernel.org and make sure you apply the (k)ubuntu evms patch, else you won't be able to mount partitions and your entire system will be fucked up.
see for how-to's here:
[http://www.ubuntuforums.org/showthread.php?t=84174](http://www.ubuntuforums.org/showthread.php?t=84174)
[http://www.ubuntuforums.org/showthread.php?t=103900](http://www.ubuntuforums.org/showthread.php?t=103900)
note: This is only necessairy if steam shows random lock-ups/freezes.

-Install the latest gfx card drivers.
see for how-to's here:
nvidia: [http://www.ubuntuforums.org/showthread.php?t=57368&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=57368&highlight=nvidia)
ati: [http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378)
note: Every time you install a new kernel you need to reinstall certain (if not all) modules. the gfx modules are one of them.

-Install the latest wine version.
sudo apt-get install wine

-Install the latest winetools version.
for download and installation: [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)
-Run winetools (type wt in console)
run base setup
install windows system software (if the msi installer doesn't install, set to win xp)
install wordviewer97 (need to set to win 98 )
set to win xp
install steam trough tested software
for more details see here, section using wt: [http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

-Run Steam (need to set to win xp)
install cs1.6
install cs:s
run wt, set to win98, set sound to oss
set cs1.6 to opengl and run cs:s with directx70 (fugly gfx but it wil run +- smooth)

-play!

sorry for fucky how-to, add comment if something doesn't work or if something isn't clear or whatever... ;)

---

### Post by DahVid on 2006-03-04
Great tutorial! WineTools really helps.. I've recently ditched Windows (For good) and I really like playing the Half-Life mod "The Specialists"
Thanks much..

---

### Post by mumushi on 2006-03-14
:) this is a great help. Now i can play more games. Thanks alot!

---

### Post by shinygerbil on 2006-03-25
OK, after ages and bloody ages of trawling the net, I finally find the answer I'm looking for :)

And it's a simple one...


"upgrade your kernel"


](*,) 


I was wondering what the whole freezing thing was all about, and now I know :P I just hope it works! I've been looking for an excuse ;)

Steve

---

