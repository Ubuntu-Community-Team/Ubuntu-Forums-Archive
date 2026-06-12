---
title: "scripting help"
date: 2006-07-26
forum: Desktop Environments
---

### Post by acke on 2006-07-26
Hey!

okej, I have a foo.ram fil (realplayer file) that contains a source link for a radio stream. for ex. 

```
  rtsp://sr-rm.qbrick.com/broadcast/cluster/encoder/foo.rm 
```

Anyone knows a good way to write a small shell script to to exract this source and run it in mpalyer? In other words i would like to run the script on the file and get mplayer to play the stream or file. 

Would be realy glad if some one could help me since I really dislike Realplayer. 

tnx in advance!

---

### Post by rupert on 2006-07-26
this should do it:

#!/bin/bash
stream=$(cat $1)
mplayer $stream
exit 0


just save it in a .sh like run.sh and start it with

./start.sh bla.ram

I only tested it with a single line in the .ram file, and it wasnt a realmedia file, but that shouldnt matter.

---

### Post by acke on 2006-07-26
Works like a charm... no more realplayer for me. tnx alot for the quick answer.

---

### Post by Thund3rstruck on 2006-07-27
You may want to add the script into ~/.gnome2/nautilus-scripts folder so you can just right click to run it against the file..

---

