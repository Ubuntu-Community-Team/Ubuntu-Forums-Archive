---
title: "how to install Quake 4 (native)"
date: 2020-04-07
forum: Gaming &amp; Leisure
---

### Post by zakko on 2020-04-07
I have downloaded and installed the package **quake 4** ([URL="https://packages.ubuntu.com/eoan/quake4"]https://packages.ubuntu.com/eoan/quake4

[/URL]Where have i to put the *.pk4 files from my Quake 4 DVD?

**home/zakko/.quake4/q4base** or **/usr/local/games/quake4/q4base** didn't work.

I always get this **Data file is missing: q4base/pak001.pk4**. message when i start quake4.

Thanks.

---

### Post by Perfect Storm on 2020-04-07
according to file list of the package, the game is installed under /usr/games/quake4

---

### Post by mastablasta on 2020-04-08
please let me know if this works. i would also like to load quake 4. i see it works in wine, but if there is an option to get it to run native it would be even better.

---

### Post by mastablasta on 2020-04-09
i got it working using original launcher/installer. 

i followed this guide: [https://www.gamingonlinux.com/articles/playing-quake-4-on-linux-in-2018.11017](https://www.gamingonlinux.com/articles/playing-quake-4-on-linux-in-2018.11017)

on install i used a premade folder as target: /home/*myusername*/quake4
for symlinks (in installer) i used the same folder.

i have renamed the two libraries that come with installer (just as mentioned in article).
i copied the config settings form the author.

though i had to leave sound setting at "default" not "hw;0,0" to get the sound working in my case. i turned surround sound of (since i have only 2 speakers). the game runs fluently on ultra in 1920x1080 on the machine i used for install. 

i also had to use the key workaround described in article. if you have a GOG copy, you have to use it because the old launcher wants the key.

i wish someone would create new launchers/installers for GOG versions. doom3 and quake4 are definitely games that should be available and running native. after so many years these games still look awesome and you can now run them at ultra settings on what these days would be considered a potato (i ran Doom 3 at full settings on single core Athlon 64 3800; nvidia GT730 -2GB; 4GB DDR2 ram).

Quake PC:
Kubuntu 18.04.4 LTS
Ryzen 7 2700
Nvdia GTX 1650 (recomended driver installed)
16GB ram

---

