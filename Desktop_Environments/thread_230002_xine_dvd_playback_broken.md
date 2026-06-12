---
title: "xine dvd playback broken"
date: 2006-08-05
forum: Desktop Environments
---

### Post by diff_sky on 2006-08-05
Hi,

Has anyone had their playback of DVDs broken in Xine recently? I had xine setup to play dvds fine (restricted formats etc) but today (after a number of system updates I guess - I saw gstreamer in there being updated) I get this error when playing a dvd that I know I've successfully watched only recently:

```

The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g. not disc in drive).
(/media/cdrom0/video_ts/vts_01_0.vob)

```

Any ideas?

---

### Post by stanwebber on 2006-08-05
from what i've been able to find out it looks like some miserable excuse for a human being decided to obsolete the totem-xine package.  dapper is so pathetic--i wish to hell i had never upgraded from breezy

---

### Post by diff_sky on 2006-08-05
OK, I think I fixed my problem.

I did two things:
```

sudo aptitude reinstall xine-ui

```

Not sure if that fixed anything. I also stopped Xine trying to play a DVD as soon as it was entered - it would error doing that but wouldn't error if I started Xine manually and asked it to play the dvd in the drive (weird).

So now I am back watching DVDs again.

I hope this helps someone else.

---

### Post by stanwebber on 2006-08-06
ok, here's the solution.  totem-xine is located in dapper universe; logically, updates will be released to dapper-updates universe.  low & behold i checked my sources.list that i got off the dapper upgrade thread & it was missing dapper-updates universe & multiverse

to fix it i changed```
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```
to```
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
```

---

### Post by tribaal on 2006-08-10
Thanks a lot for the sources.list fix, it solved it all for me :)

Cheers!

- trib'

---

