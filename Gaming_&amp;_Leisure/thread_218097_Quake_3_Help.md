---
title: "Quake 3 Help"
date: 2006-07-18
forum: Gaming &amp; Leisure
---

### Post by andy- on 2006-07-18
Fresh install, I made a mistake clicking on 'Play now' I'm thinking thats what screwed this up. 

[COLOR="DarkOrange"]andy@home:~$ ioquake3
./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
andy@home:~$[/COLOR]

I tried: [COLOR="DarkOrange"]sudo chown -R <username>:<username> /home/<username>/./ioquake3.i386[/COLOR]
But the folder isn't there. Not sure what to do, I'm still fairly new to this. 

Thanks.

---

### Post by scxtt on 2006-07-18
it wouldn't be:

**sudo chown -R <username>:<username> /home/<username>/./ioquake3.i386** 

it would be:

**sudo chown -R <username>:<username> /home/<username>/.ioquake3.i386**

and make sure you've installed the libopenal library:

**sudo apt-get install libopenal0a**

---

