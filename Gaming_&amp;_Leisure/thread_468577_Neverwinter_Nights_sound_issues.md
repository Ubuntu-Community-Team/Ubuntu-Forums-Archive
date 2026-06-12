---
title: "Neverwinter Nights sound issues"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by Tyke91 on 2007-06-09
I have had this issue before and tried to solve it using a fix on the nwn.bioware forums.

(changing the nwn file to look like this

```
#!/bin/sh
# change to the nwn directory

cd $(dirname $0)

# set enviroment variables

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
export SDL_AUDIODRIVER=esd

# set library search path

export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

# fire up the game
./nwmain $@

```


this seemed to work at first, but unfortunately, the problem resumes after just 15 minutes or so of playing the game.

The games sounds becomes increasingly stuttery as this progresses. progressing from barely noticeable to ZOMGZ!TIHS 50UND SUXXORZ!!!!!!!!! in around 2 minutes after it starts 


anyone know how to fix this?

---

