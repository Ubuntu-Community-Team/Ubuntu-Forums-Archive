---
title: "Anyone good with xplanet and gconf?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by TeeAhr1 on 2006-07-20
I'm trying to use a script that I found in the O'Rielly Ubuntu Hacks book to retrieve an image of my city from xplanet and use it as my background.  Of course, I'm running blind here, because I don't understand the subject matter in the least.  Here's the script, as written in the book:
```
#!/bin/sh
rm -f /tmp/earth-*.jpg;
IMAGE=/tmp/earth-\Qdate +%s\Q.jpg;
nice xplanet -num_times 1 -output $IMAGE -geometry 1280x1024 \\
-longitude 93 -latitude -45;
gconftool -t string -s /desktop/gnome/background/picture_filename $IMAGE;
```
I save this file in home as xplanetbg.sh and try to run it.  Here's what pops out:
```
xplanet.sh: line 3: +%sQ.jpg: command not found
Error: unrecognized options: 1280x1024 \
Perhaps you didn't supply an argument to -output?
Exiting from Options.cpp at line 914
xplanet.sh: line 5: -longitude: command not found
No value to set for key: `/desktop/gnome/background/picture_filename'

```
It seems to my untrained eye that several things are apparently wrong with my script, but damned if I know what they are.  (I told you I don't know what I'm doing.)  Can anyone give me some guidance on this obviously life-or-death issue? :rolleyes: 

Also, I would then like to be able to automagically run this script every half hour.  If anyone can help me do that, that'd be great too.  Cheers...

-pete

---

