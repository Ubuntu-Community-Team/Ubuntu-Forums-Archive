---
title: "dpkg-reconfigure x11-common Diablo 2"
date: 2014-07-28
forum: Gaming &amp; Leisure
---

### Post by Mark_in_Hollywood on 2014-07-28
I can't get Blizzard's Diablo II (Diablo 2) to run full screen. I have installed the "glide" and read here:

[http://ubuntuforums.org/showthread.php?t=1937317&highlight=dpkg-reconfigure+x11-common+Diablo](http://ubuntuforums.org/showthread.php?t=1937317&highlight=dpkg-reconfigure+x11-common+Diablo)

I ran the Blizzard "videotest.exe" and the choice given was the glide-3dx (approx. name - memory lapse) and have rebooted the 'puter. No joy.

At WineHQ, there is a post about using

dpkg-reconfigure x11-common

and running a script

q.v. [https://appdb.winehq.org/objectManager.php?sClass=version&iId=25602&iTestingId=54269](https://appdb.winehq.org/objectManager.php?sClass=version&iId=25602&iTestingId=54269)

Is it safe, smart, sensible to reconfigure a working, stable 14.04.1 with the script and the reconfigure?

Here's the short script:

```
If you use ubuntu/debian, reconfigure x11-common packagage to allow all users to run a new X session.

# dpkg-reconfigure x11-common

Choose Anybody.

To run the game you can write a script so you call it from the gnome menu. An example is given here.

#! /bin/bash
# Run Diablo 2 on other X instance
export LAST_PWD=$PWD # Saves you last working path
cd /media/disk/drive_c/Games/Blizzard/Diablo\ II/ #Goes to your diablo 2 install path
xinit /usr/bin/wine "Game.exe" -- :1 vt9 # runs diablo 2 on a new X session at screen 1, on virtual terminal 9.
cd $LAST_PWD # On diablo exit, returns to your last working path.
exit 0
```

---

### Post by mastablasta on 2014-07-31
not sure what the issue is. The game doesn't start?
FAQ: [http://www.svenswrapper.de/english/other.html](http://www.svenswrapper.de/english/other.html)

I have to check how I have it running. it oculd be it is windowsed but with windows removed. can't remember now. I  know It gave me problems in Gnome on 10.04, full screen ran but panels were showing. I do not have this issue now in KDE. hm...

---

### Post by Mark_in_Hollywood on 2014-08-02
It took 6 hours of searching and experimenting but this post/thread had the solution.

[http://ubuntuforums.org/showthread.php?t=1211673](http://ubuntuforums.org/showthread.php?t=1211673)

---

