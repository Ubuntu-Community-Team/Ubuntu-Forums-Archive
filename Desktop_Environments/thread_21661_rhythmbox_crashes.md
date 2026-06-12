---
title: "rhythmbox crashes"
date: 2005-03-23
forum: Desktop Environments
---

### Post by BigCdaAnswer3 on 2005-03-23
i had rhythmbox working ever since i first installed ubuntu, and i use it all the time...
today when i tried to open it, it crashed! Here is the output i got from the terminal:

Rhythmbox-ERROR **: file rb-ipod-source.c: line 478 (rb_ipod_get_itunesdb_path): assertion failed: (mount_point != NULL)
aborting...

 8-[

---

### Post by ejlozon on 2005-03-24
when it crashed, was there an audio CD in the drive?

---

### Post by e.j. on 2005-03-24
I'm having the exact same problem, and I have a CD in the drive when I start it up. I haven't tried sans-CD yet.

---

### Post by sbaker33 on 2005-03-25
rhythmbox crashes on me as of today (never did before) I am getting this error:
"Failed to create the player: Couldn't initialise scheduler. Did you run gst-register?"
No audio CD

Any ideas?

---

### Post by wylfing on 2005-04-12
I encountered this error when I installed the pymusique debs. I cleared it up by running this:
```
/usr/bin/gst-register-0.8
```
HTH

---

