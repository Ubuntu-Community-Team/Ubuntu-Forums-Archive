---
title: "screwed on 28th mount"
date: 2008-01-02
forum: Dell  Ubuntu Support
---

### Post by teogearloose on 2008-01-02
Caught in vicious circle:

During startup, I get:

[INDENT]* checking root file system
fsck 1.40.2 (12-Jul-2007)
os_part has been mounted 28 times without being checked  check forced
[/INDENT]
and somewhere beyond 15% of the forced check everything hangs

[same result if I grub recovery mode]
 
Can I bypass the forced check and ensuing disaster?

---

### Post by ajgreeny on 2008-01-02
Try booting the liveCD and then using fsck on the hard disk ubuntu partition from there.  Make sure the ubuntu partition is unmounted before you try as you can't fsck a mounted partition at all.
If all this is new to you have a look at the manual ```
man fsck
```and it will tell you all you need to know to run it and if there are problems how to try to put them right.

Good luck.

---

### Post by notwen on 2008-01-02
I've had this happen to mea couple of times, simply use a LiveCD to run fsck as ajgreeny recommends and all should be well once fsck completes.  Just curious what model Dell you happen to be running?

---

### Post by teogearloose on 2008-01-02
Thanks, guys. That's what I really needed - a link to a useful tutorial. Machine's an Inspiron 1420; just moved up to 7.10.

---

### Post by notwen on 2008-01-03
Glad you got it working.  I have a 1420n myself, will be waiting for a few before I upgrade w/ the new Dell-buntu Gutsy iso.  =]

---

