---
title: "The Devil Whiskey"
date: 2006-08-29
forum: Gaming &amp; Leisure
---

### Post by leech on 2006-08-29
Ok, I know Artificial Intelligence has this game, and that he wrote a how to on getting it to work for Dapper, but I still have problems with it.

Granted right now I'm running Debian Sid.  When I first ran the game, it ran ok, but spat out some Python error messages.  Then after reading AI's how to, it said that it uses Python2.2.  So I had to enable the Etch repositories, since Sid no longer has Python2.2 in it.  

After installing it the game loaded, and runs, but as soon as I get into any encounters that then have treasure, the game crashes.  Well, the treasure screen comes up, but then after I take it all, it crashes with this error;

```
Traceback (most recent call last):
  File "<string>", line 1, in ?
  File "/usr/lib/python2.2/random.py", line 76, in ?
    from math import log as _log, exp as _exp, pi as _pi, e as _e
ImportError: /usr/lib/python2.2/lib-dynload/math.so: undefined symbol: PyFPE_jbuf
Segmentation fault
```

The game looks sweet, and I'd rather not have a game that cost 30 bucks that I can't play.  I guess I could always play in Windows... but that was one of the reasons I got the game is because it runs in Linux.  

It gave different errors when I ran it with python2.4, if those would help, I can remove python2.2 and get the output again.  I also could not find the 2.01a patch, not sure if they released it for linux or not.  If all else fails, I can try emailing support, but it didn't look like that was too active (at least their forums aren't.)

Leech

---

### Post by Perfect Storm on 2006-08-29
What I know is there's a bug in Python2.2 which might make some weird stuff happen in The Devil Whiskey (I've checked a bug report on Debian), but I don't know if it have been correctly (in the light it's old).
I think the linux version is = 2.0 windows version. I don't have the game installed at the moment so I'm not sure.

---

### Post by leech on 2006-08-29
Yeah, it says it's the 2.0 version, so I don't know if they released a patch for the newer version or not.  

I initially had the Ubuntu dapper python2.2 package installed and it gave the same error.

I'll try sending them some email and see if they reply.

Leech

---

