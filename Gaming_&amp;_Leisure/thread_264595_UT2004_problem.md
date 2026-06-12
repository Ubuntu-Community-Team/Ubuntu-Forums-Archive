---
title: "UT2004 problem"
date: 2006-09-24
forum: Gaming &amp; Leisure
---

### Post by CAUSTICROUTER on 2006-09-24
I recently migrated to ubuntu, and I am a big gamer.  I installed UT2004, but have one problem.  I want to play on servers with custom maps, but, the ingame download doesn't work correctly.  It downloads, then pauses and crashes to desktop at the load screen(that you would normaly get when loading a map IE: loading...dm-rankin). I can think of two things that could be the problem, the game might not have write permission, or the maps are being saved to the .ut2004 folder instead of the ut2004 one.  I think the second one would cause a problem, but is not the problem at the moment, because in the .ut2004 folder, there is no maps.  I read in the readme that you can change where the game saves by typing nohomedir in the command line, but, it does nothing.  I think i need to give the game write permission AND change where it saves, but am not sure how to go about doing either of those.

---

### Post by ceil420 on 2007-06-19
Did you ever find the solution? Or does anyone know what's up? Someone just asked about the same problem in IRC, and this thread is the only thing I've been able to find so far :x

Haven't asked him what specific distro he's got; he just said he has Ubuntu.

---

### Post by Cappy on 2007-06-19
```

chown $USER:$USER -R ~/.ut2004
chmod 774 -R ~/.ut2004

```
may fix this problem

---

