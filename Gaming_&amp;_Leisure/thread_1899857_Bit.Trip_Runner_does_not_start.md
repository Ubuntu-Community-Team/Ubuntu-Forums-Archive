---
title: "Bit.Trip Runner does not start"
date: 2011-12-24
forum: Gaming &amp; Leisure
---

### Post by hero1900 on 2011-12-24
i got it from the HIB4 and whenever i start it i got this

```
/bit.trip.runner: /usr/lib/i386-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by ./bit.trip.runner)
```which is installed and exist i did locate it and the libstdc++6 already installed so what is the problem with the version??


i solved it i found a topic about it but its not detailed so if any one has this prblem here what he can do
first go to this link and download the deb package for your system 32 or 64 [http://packages.ubuntu.com/oneiric/libstdc++6](http://packages.ubuntu.com/oneiric/libstdc++6) open it by archive manager and extract the files in libs forlder (2 files libstdc++.so.6.0.16 libstdc++.so.6) and then copy those two files to your game folder and after that before you launch the game enter this command in terminal 
export LD_LIBRARY_PATH=~/Games/bit.trip.runner-1.0/bit.trip.runner  (or whatever you have it)
you have to do this each time you log in and out of your user or you make a shell script that do that for you automatically and run the game as following make a new file and paste this and then make it as executable and copy it to the game folder and run it

#!/bin/sh
GAMEPATH=`readlink -f "$0"`
BIN=bit.trip.runner
cd "`dirname "$GAMEPATH"`"
export LD_LIBRARY_PATH=$GAMEPATH:"$LD_LIBRARY_PATH"
echo $LD_LIBRARY_PATH
$BIN $@

---

### Post by Jozza The Wick on 2012-04-23
Thanks very much for this! I'd downloaded Bit.Trip.Runner from the Humble Bundle but hadn't been able to get it to to work until now. I just wanted to point out that even on earlier versions of Ubuntu, you need the package for Oneiric, not your own distribution. Specifically, you need libstdc++.so.6.0.16 (and the link libstdc++.so.6) for the game to work. I had libstdc++.so.6.0.13, but the game didn't work until I copied libstdc++.so.6.0.16. Even though you won't be able to install the deb package (on earlier versions of Ubuntu) you can still open it with the Archive Manager and extract the files that way.

Thanks again, hero1900!

---

