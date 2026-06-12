---
title: "gmplayer config?"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-07-09
So if I run mplayer <filename> it runs the video no sweat. But if I right click in gnome and select "Mplayer Movie Player", I get the error initializing --vo output device. 

I tracked down the /usr/share/applications/mplayer.desktop file and its actually calling gmplayer. If I replace gmplayer with mplayer it works, however there are no controls for pause, FF, rewind, etc. 

Where is the gmplayer config file? According to the locatedb there isn't one??

Thx,
T3

---

### Post by taurus on 2006-07-09
Look in ~/.mplayer for all the config files...

---

### Post by Anduu on 2006-07-09
I suspect it is because gmplayer is trying to use a different video output than mplayer....

Right click anywhere on the gmplayer window and select preferences.

Go to the video tab and check which output it is using...try changing it and see what happens.

I get best results using "XV" or "gl2"

---

### Post by Thund3rstruck on 2006-07-10
Hey thanks for that. Yea, the mplayer configs were all set right which is why mplayer worked fine. I still haven't found the gmplayer config file, but editing the Video filter settings in gmplayer itself did the trick. 

Thanks

---

### Post by taurus on 2006-07-10
Gmplayer is reading the config files in ~/.mplayer!!!

---

### Post by Thund3rstruck on 2006-07-10
@taurus

Sorry about that man... I need to work on my attention to detail...

You posted ~/.mplayer, I saw /etc/mplayer...

Thanks for the assitance though,
T3

---

