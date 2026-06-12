---
title: "Empty when receiving files from MSN 7.5 with Kopete"
date: 2006-01-09
forum: General Help
---

### Post by Al_maverick on 2006-01-09
I started having this problem. When I receive files from MSN 7.5 clients, the download works fine, but when it ends, the file is empty (0 bytes).
I found this bug report in KDE.org. [http://bugs.kde.org/show_bug.cgi?id=113525]("http://bugs.kde.org/show_bug.cgi?id=113525")

Anyone knows of a workaround? In my country most people use MSN.

Thx in advance!
Al

---

### Post by JLTB on 2006-01-11
Me too.

Half the staff in my office is on MSN Messenger for Mac, the other half is on MSN Messenger for Windows.  Both can send me files, but they end up as 0 bytes (however the files do transfer).

Me thinks the bug is as simple as the temp file data not being moved to its final resting place.

---

### Post by Pekkalainen on 2006-01-11
Confirmed here too, and it is the most annoying bug in the history of Linux :mad:

---

### Post by ace2005 on 2006-01-11
Well for me after the download has started the speed keeps slowing down and then stops in the middle, i have to keep switching to amsn

---

### Post by depp on 2006-01-12
Same here. Wanting a fix!

---

### Post by tigrez on 2006-01-12
Maybe the 6891 port. 
Do you have tryied to open it in your router?

---

### Post by ace2005 on 2006-01-13
[QUOTE=tigrez]Maybe the 6891 port. 
Do you have tryied to open it in your router?[/QUOTE]

Doesn't make a difference, http method of connecting doesn't help either

Anyone know how to make it use the old transfer method? maybe a compile thing?

---

### Post by beast2k on 2006-01-13
I had the same trouble it seems theres no fix yet. I used synaptic and installed aMSN it works great and is alot like the real MSN, it's good for now untill they release a fix or new version.

---

### Post by Al_maverick on 2006-01-13
[QUOTE=ace2005]Doesn't make a difference, http method of connecting doesn't help either

Anyone know how to make it use the old transfer method? maybe a compile thing?[/QUOTE]

According to the bug comments in kde.org (check the link in the first post), versions 0.11+ have this problem. Version 0.11 was the one bundled in kde 3.5. And the version compiled from source in SVN have this problem too.
Version 0.10.3 seems to be free of problems :) , but you have no cam support and other features included in 0.11 :(

---

### Post by Al_maverick on 2006-03-06
According to the bugzilla in kde, a patch has been released, but it is still being tested, and it looks like they found some problems with transfers from clients other than msn.
Anyway, it still isnt packaged, if you want to try it, you should download the source and compile it from scratch.

---

