---
title: "CS:Source crashes while shooting"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by frostedegg on 2007-05-10
I am new to linux and wine, but I managed to get steam and source running.  I can join games, sound works good, etc etc.  The only problem I have is that everything will freeze up sometimes while I am shooting.  Terminal displays the following:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  144 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x320084d
  Serial number of failed request:  10114
  Current serial number in output stream:  10114

Mobility X700 graphics card.  ATI proprietary drivers.  Any help?

---

### Post by misfitpierce on 2007-05-10
Maybe try purchasing cedega if it means that much to ya... Runs fine for me on cedega.

---

### Post by calgarystevens on 2007-05-10
Well, I run CS Zero without a problem (most always) on an ATI Xpress 200M laptop so I can't really say what could be causing that. The only thing that comes to mind would be perhaps a memory related problem. Maybe wine is only seeing your shared memory as 32 not 128 mb or something. Try this post (unrelated to wine/steam I know, but hey) [http://ubuntuforums.org/showthread.php?t=150854](http://ubuntuforums.org/showthread.php?t=150854) You can also add the heapsize option to your steam startup shortcut I think to give it more memory to play with.

---

### Post by LollYouSuckZor on 2007-05-10
I thought cegeaga or whatever... was free..

---

### Post by MikeReiner on 2007-05-10
Well cedega doesn't even work for me. Steam freaks out and wont show my list of games, and even when it does, it wont let me join or create any servers. Doesn't exactly seem to be worth the money.

---

