---
title: "Anyone know how to cheat at nethack?"
date: 2007-11-16
forum: Gaming &amp; Leisure
---

### Post by earobinson on 2007-11-16
All I want to do is to be able to do the [save game chea]("http://www.gamespot.com/pc/rpg/nethack/hints.html")t but it dont seem to work for me I have even tried copying the whole /var/nethack directory.

Any help?

I'm using nethack-gnome

Thanks

---

### Post by KhaaL on 2007-11-16
I might be way off, but aren't the savegames recorded in your home folder? 

I play a little nethack myself from time to time, good to see others into rougelikes today! :)

---

### Post by earobinson on 2007-11-16
Figured it out
**Code to backup**
```

rm -rf nethack.bak
cp -ra nethack nethack.bak

```

**Code to restore**
```

rm -rf nethack
cp -ra nethack.bak nethack

```

---

