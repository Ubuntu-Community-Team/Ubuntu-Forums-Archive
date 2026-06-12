---
title: "Kaffeine won't open video files directly from nautilus"
date: 2008-08-31
forum: Debian
---

### Post by benerivo on 2008-08-31
When i try to open any video file from nautilus, kaffeine gives the following error message> The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/home/andrew/video.avi)and then gives the following xine errors> No plugin found to handle this resource (dvd:/home/andrew/video.avi)
10:53:01: xine: cannot find input plugin for MRL [dvd:/home/andrew/video.avi]
10:53:01: xine: input plugin cannot open MRL [dvd:/home/andrew/video.avi]
10:53:01: xine: found input plugin : DVD NavigatorIt seems to think that it is a DVD disc that i am trying to play, but these files are just on a hard drive partition. When opening any video file from within kaffeine there are no problems at all. There are no such problems with audio files. This is on debian unstable.

EDIT -It also has this probelm when opening from dolphin, or a terminal (ie. kaffeine /home/andrew/Desktop/video.avi)

---

