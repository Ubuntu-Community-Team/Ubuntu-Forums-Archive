---
title: "OnTV Issues"
date: 2005-11-03
forum: Desktop Environments
---

### Post by binarymelon on 2005-11-03
After installation of ontv when I try and add it to the panel it doesn't appear, but when I run ps -ef | grep ontv I get the following:

ryan      8384     1  2 18:28 ?        00:00:00 python /usr/lib/ontv/ontv --oaf-activate-iid=OAFIID:GNOME_OnTVApplet_Factory --oaf-ior-fd=55

Is there anywhere I could see some output that might explain what the problem is?

---

### Post by binarymelon on 2005-11-04
bump

---

### Post by rel on 2006-02-18
Same here!

This has been ans issue for ages. Had the same trouble with it back when
using gentoo.

Wonder how many people running dapper have the same?

-rel

---

### Post by binarymelon on 2006-03-03
I'm using it in dapper now and it works perfectly.

---

### Post by phorque on 2006-05-04
So how do you get it to actually run? I tried "./ontv" in the /usr/lib/ontv/ directory but nothing appears

---

### Post by conedude13 on 2006-05-05
Have you tried it either with sudo or as root?

---

### Post by phorque on 2006-05-07
[QUOTE=phorque]So how do you get it to actually run? I tried "./ontv" in the /usr/lib/ontv/ directory but nothing appears[/QUOTE]

d'oh, it's actually something you add to your GNOME panel. It's just available when you use "add to panel" after install. (n00b)

---

