---
title: "Screen Saver Fix?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by Nibiruet on 2006-07-29
Has the bug with the screen saver in Dapper been fixed? Tried many of the so called "fixes" soon after v6.0.6 came out with no luck.

If someone has used a fix with success please provide link to Post or URL - thanks!

---

### Post by Anduu on 2006-07-29
What bug?

---

### Post by Rastareefer on 2006-07-30
If you are refering to the non starting screen saver bug, I have tried 3 fixes non of which seem to work on Kubuntu 6.06 LTS

This is the latest one I tried 30 mins ago.
Maybe I didn't do it right.
If you try it and it works, please post about it.

------------------------------------------------------------------------
This Gzipped Tar archive fixes the Screensaver problem in Kubuntu 6.06 ([https://launchpad.net/bugs/52142](https://launchpad.net/bugs/52142)) and KDE 3.5.3 ([http://bugs.kde.org/show_bug.cgi?id=128610](http://bugs.kde.org/show_bug.cgi?id=128610)) in general.

NOTES:
The binaries contained within the package are built against KDE 3.5.3 (kdebase_3.5.3-0ubuntu0.2).

You MUST be using that specific KDE version of Kubuntu to ensure maximum stability.

On the other hand, you could also use this with kdebase_3.5.3-0ubuntu0.1 but use it at YOUR OWN RISK.

INSTALLATION:
1. Go to the directory where the package has been downloaded.
2. Execute the following command:
sudo tar -xvvzf kdesktop_3.5.3-0ubuntu0.2_FIX_i386.tar.gz -C /

ADDITIONAL NOTE:
Bug 49228 has already been fixed (by me of course. :D). Point your browser to [https://launchpad.net/bugs/49228](https://launchpad.net/bugs/49228) to see the fix.

---

