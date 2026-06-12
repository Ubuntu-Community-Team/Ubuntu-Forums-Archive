---
title: "Problem with track duplicates in amaroK."
date: 2005-09-03
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-09-03
While I love amaroK, I hate its errors.  Currently, all of my tracks are duplicated about 100 times each in amarok.  I don't know how many tracks there are total, but it got up to just Daft Punk when i was adding them all to my playlist and it was already at 2000+ tracks (which I have maybe 50 from A-D).  

Here is a screenshot of my music collection in amaroK and my /home/john directory (where my music is, i need to reorganize >_<) in konqueror:

[http://arcanis.is-a-geek.com:81/error.png](http://arcanis.is-a-geek.com:81/error.png)

As you can see, I have about 50 or so odd copies of the track "Judas Rising" when I only have one physical copy in my music directory.  

This is driving me crazy, just having amaroK open makes my computer lag horribly.  How do I fix this???

Thanks ALOT to anyone who helps.

---

### Post by arcanistherogue on 2005-09-04
Bump...  ](*,)

---

### Post by arcanistherogue on 2005-09-05
Bump 
Up
My 
Post

---

### Post by greyhound4334 on 2005-09-05
I've had some weird problems with my amarok collection.  At one point, I switched  to using mysql instead of the built-in sqlite.  It helped with some weirdness in the collection and sluggish playback.  Currently, I'm running 1.2.4 with sqlite with no problems.

A couple of suggestions:

1. you might try switching to mysql if you have mysql running somewhere.  Easy if it's already running, probably a pain if you have to install it.
2. what version are you running?  1.2.4 is included in breezy.  I don't know if you can install it into hoary without running into dependency problems, but you might be able to build it from source.
3.  you might try deleting the amarok configuration directory (somewhere under /home/john/.kde -- I'm too lazy to look, but shout back if you can't find it).  Then rerun it and rebuild your collection.
4. you might try posting on the amarok forum:
[http://amarok.kde.org/component/option,com_simpleboard/Itemid,57/func,showcat/catid,8/](http://amarok.kde.org/component/option,com_simpleboard/Itemid,57/func,showcat/catid,8/)
5. you might try looking in bugzilla:
[http://bugs.kde.org/](http://bugs.kde.org/)

Hope some of that is helpful.

---

