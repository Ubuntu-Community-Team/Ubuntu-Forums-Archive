---
title: "Metacity and DualScreen setup"
date: 2006-07-31
forum: Desktop Environments
---

### Post by thieummm on 2006-07-31
Hi all,

I have two displays: one LCD panel and one videoprojector, both plugged in a NVIDIA Geforce MX card. EVerything works fine with X (using nvidia prop drivers)....

BUT, as I use my videoprojector only to watch movies, it is turned off most of the time. The problem is that when I launch new programs, the windows often appear on the videoprojector part of the screen... So every time it happens I have to use the "move" function to make it appear on the LCD screen  ;-P

I can't seem to find any options that could "tell Metacity to always open the new windows on the LCD part of the screen"....

Does anyone know how to do that ? 

-> I used to use KDE and Kwin and there was an option like "Open new windows on the screen containing the pointer".... but what about Gnome and Metacity ?


Thx.


Mathieu.

---

### Post by it.henrik on 2006-07-31
hmm .. my dualscreen setup always opens my window where the pointer is.

What you might want instead is maybe to start a new x-session for the movies you want to watch.

I have something similar for my tv-out .. a script called tvout

I just run 

tvout name_of_movie.mpg 

to get a nice crisp vlc movie playback on my tv-out.

---

