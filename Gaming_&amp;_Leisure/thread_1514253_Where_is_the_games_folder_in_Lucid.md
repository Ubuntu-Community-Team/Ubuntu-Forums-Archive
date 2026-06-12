---
title: "Where is the games folder in Lucid?"
date: 2010-06-20
forum: Gaming &amp; Leisure
---

### Post by bwallum on 2010-06-20
I have a game installed called Osmos. It currently runs from my Desktop. I would like to put the files in a folder better associated with games. Where is the games folder?

---

### Post by J.K.Makowka on 2010-06-20
There is none by default, just make one in your home directory.

---

### Post by hikaricore on 2010-06-20
The official deb package should install in the /opt directory.
Did you extract it from another type of archive or perhaps steal it?

---

### Post by bwallum on 2010-06-21
> **hikaricore said:**
> The official deb package should install in the /opt directory.
Did you extract it from another type of archive or perhaps steal it?
It was a gift for Father's Day. I have learnt that it is a commercial package in another thread today. How do I check if it is 'genuine' commercial software. Is there a way of paying for it if it isn't 'genuine'? I don't want to embarrass anybody and I don't do 'steal'

---

### Post by ronnielsen1 on 2010-06-21
Mine (demo - not stolen either) installed in /opt/OsmosDemo. Games usually install in /opt or /usr/games. If your installed version is in /opt/Osmos instead of /opt/OsmosDemo you probably have a legitimate full copy. Without buying it I can't experiment to see if it's stealable

---

### Post by hikaricore on 2010-06-21
Osmos has no drm or anything of that nature, it's plenty stealable and there's no way to really tell if your version is legit.
As long as you trust whoever gave it to you has bought it then I wouldn't worry about it.
If you find out it isn't legit you could always goto the Osmos site and purchase a download copy.  :p

---

### Post by bwallum on 2010-06-22
I installed it in /opt, well installed is a rather overstated simply created a directory and put the files in. I then used 'Edit Menus' to point to the binary file that starts it (using sh in front of the path).

Nice enough game, when's the three dimensional version coming out? I would like to model dipole evolution with something like that!

---

### Post by J.K.Makowka on 2010-06-22
> **bwallum said:**
> I installed it in /opt, well installed is a rather overstated simply created a directory and put the files in. 

This is not recommended. Unless you have a .deb which automatically installs files in these directories you should put all programs and files you installed "by hand" in your home directory (in this case for example in a games sub directory).
There is a reason why you can access those directories without the administrator password, and for the security of your computer those system directories should be left untouched.

Linux is save by design, but not if you brake that security intentionally.

---

### Post by bwallum on 2010-06-22
OK, Osmos was purchased online so hope that resolves that issue, I've installed it in /home/bob/ManuallyInstalled/games/osmos.

Are we all happy now! "You bet your life we are..." unless of course you know differently....

EDIT
...and I will donate a further $10 to the open software folks nominated by your goodselves upon which Osmos undoubtedly used in building their commercial software. Did I hear an earlier comment about theft?

---

### Post by ronnielsen1 on 2010-06-23
=d>> ...and i will donate a further $10 to the open software folks nominated  by your goodselves upon which osmos undoubtedly used in building their  commercial software. Did i hear an earlier comment about theft?

---

