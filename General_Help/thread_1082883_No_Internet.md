---
title: "No Internet"
date: 2009-02-28
forum: General Help
---

### Post by metalhead0010 on 2009-02-28
I'm stuck on the commandline without any Internet so lynx failed on me and when I tried to fix my problem by downloading something I lost Internet.  How do I get Internet without the GUI?

---

### Post by Iowan on 2009-02-28
Depending on how your network is set up, **dhclient** *might* resurrect connection.  */etc/init.d/networking restart* is useful after changing configuration - it might be another option.  These *might* get the network interface going - getting to Internet from there ???

---

### Post by metalhead0010 on 2009-03-01
It should work but it didn't.

---

### Post by metalhead0010 on 2009-03-03
I found out why.  It's because my networking is disabled, how do I reinable it?

---

### Post by metalhead0010 on 2009-03-07
Got the Internet back up.  To enable it I used ... ummm I'll post the command later.

---

