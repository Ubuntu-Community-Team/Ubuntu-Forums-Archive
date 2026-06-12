---
title: "NowPlaying Screenlet + Jaunty"
date: 2009-05-04
forum: General Help
---

### Post by slag on 2009-05-04
The issue posted [here](http://ubuntuforums.org/showthread.php?t=1118798) from Jaunty beta was never resolved.  The NowPlaying screenlet doesn't work in Jaunty, although it seems to have worked with previous versions of Ubuntu.

Probably a Screenlets issue, rather than an Ubuntu one.  But if anyone around here has an idea for repairs, please share...

---

### Post by slag on 2009-05-04
Poking around a bit uncovered a modified NowPlaying module, which works for me with Exaile.

See [this post](http://forum.compiz-fusion.org/showpost.php?p=71304&postcount=4).

---

### Post by bhyman on 2009-06-03
This has been driving me bonkers as well.  Running Jaunty/RhythmBox, my Now Playing screenlet never showed cover art.  It appears as if Rhythmbox has moved where the cover art is stored.  I fixed it by running the following commands (note: the first two commands are only needed if the ./gnome2/rhythmbox directory is missing):
```

cd ~/.gnome2
mkdir ./rhythmbox
ln -s ~/.cache/rhythmbox/covers ~/.gnome2/rhythmbox/covers
```
All it did was create a symbolic link in the old location to the new Rhythmbox cover art directory.  Worked like a champ for me.  I am running Jaunty 64-bit and this was an easy fix.

---

### Post by markprice on 2009-06-04
Try deleting or renaming /usr/lib/python2.6/dist-packages/screenlets/plugins/mpdclient2.py and .pyc files. 

My now playing wasn't showing any data from Rythmbox and this fixed the problem. I got this information from [https://bugs.launchpad.net/screenlets/+bug/373438](https://bugs.launchpad.net/screenlets/+bug/373438)

---

### Post by mykrob on 2009-06-26
> **markprice said:**
> Try deleting or renaming /usr/lib/python2.6/dist-packages/screenlets/plugins/mpdclient2.py and .pyc files. 

My now playing wasn't showing any data from Rythmbox and this fixed the problem. I got this information from [https://bugs.launchpad.net/screenlets/+bug/373438](https://bugs.launchpad.net/screenlets/+bug/373438)

that worked for me too, thanks!

---

### Post by southerngrey on 2009-07-30
Confirming that this solution works.  Screenlet needs to be restarted then becomes 100% functional..  Good work!!

---

### Post by KevinLWright on 2009-08-18
THANK YOU SO MUCH!!! Was driving me crazy.

---

### Post by Felliph3 on 2009-09-02
> **markprice said:**
> Try deleting or renaming /usr/lib/python2.6/dist-packages/screenlets/plugins/mpdclient2.py and .pyc files. 

My now playing wasn't showing any data from Rythmbox and this fixed the problem. I got this information from [https://bugs.launchpad.net/screenlets/+bug/373438](https://bugs.launchpad.net/screenlets/+bug/373438)



Finally found a solution to make it work! Thanks man.

---

### Post by jkid on 2010-07-21
how do i delete the files!!

---

