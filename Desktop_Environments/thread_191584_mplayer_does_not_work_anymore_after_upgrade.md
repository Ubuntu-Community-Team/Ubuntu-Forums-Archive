---
title: "mplayer does not work anymore after upgrade"
date: 2006-06-07
forum: Desktop Environments
---

### Post by supermarchino on 2006-06-07
to dapper. gives an unreadable error. in breezy worked falwlessly.

---

### Post by Zymous on 2006-06-07
I have the same problem. It works from the command line and as a Firefox plugin though.

-- 
Zym

---

### Post by linuchsan on 2006-06-07
So what does gmplayer say when run from a terminal?

---

### Post by Zymous on 2006-06-07
There's another similar thread here [http://www.ubuntuforums.org/showthread.php?t=187799&highlight=mplayer](http://www.ubuntuforums.org/showthread.php?t=187799&highlight=mplayer) and I was able to (partly) sort out my problems by adding a default skin and changing vo from xv to x11.

The video won't play fullscreen, but that's something to work on.

-- 
Zym

---

### Post by supermarchino on 2006-06-08
solved. there was no installed skin at all (dependencies issue? :roll: )

---

### Post by morequarky on 2006-06-08
I suggest removing mplayer and it's dependancies and reinstalling them.  worked for me when I had that issue.

---

