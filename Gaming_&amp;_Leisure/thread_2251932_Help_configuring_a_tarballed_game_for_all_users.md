---
title: "Help configuring a tarballed game for all users"
date: 2014-11-07
forum: Gaming &amp; Leisure
---

### Post by redvenomweb on 2014-11-07
I have an old free (as in lunch) game that I would like to install in Ubuntu 14.04 for all users; it was distributed as a tarball.  I currently have the game in a subdirectory under /usr/games.  The problem is that this game needs to have a working directory set in order to run properly (game assets, config file, high scores file).  I have an old launcher that I made for 10.04 that uses **gnome-terminal** with the **--working-directory** and **-e** options to resolve this issue, like so:

gnome-terminal --working-directory /usr/games/foogame -e /usr/games/foogame/foostart

However, while the game can access the necessary assets, it cannot modify the config file or high score table.  What permissions should I set on these files in order to allow modification?  Should I set permissions on just those two specific files, or on the entire game folder?

Additionally, in order to run this game with sound in 14.04, I need to install the **alsa-oss** package and run the game this way (from the foogame directory):

**alsa-oss ./foostart**

What's the best way to integrate this with the working directory requirement?

---

