---
title: "Backup Question"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by FlyingIsFun1217 on 2008-02-26
Hey!

I've finally got my computer configured really nice (Artwork, Applications, etc.), and I would love to back it up, as I would with APTonCD.

Thing is, it seems that APTonCD does not back up everything I'd want it to. For example, it doesn't backup any changes I've made to GTK (macmenu project), or themes, correct?

Is there any way I can back all this up so that I could essentially just patch a new system with all of my changes?

Thanks!
FlyingIsFun1217

---

### Post by Sam Lars on 2008-02-26
There are lots of backup programs out there.
I personally use rsync to back up the directories I need backed up regularly, and keep copies of themes and config files.

---

### Post by FlyingIsFun1217 on 2008-02-27
But how exactly do I know what directories to back up? Thats why I was hoping there was something that found differences between a fresh install and a set-up system, and would save said changes.

Thanks again!
FlyingIsFun1217

---

### Post by Sam Lars on 2008-02-27
rsync automatically looks at the timestamps and syncs anything that has changed since it last saved a copy, deletes anything that no longer exists, etc.
So when it backs up my 40 GB of music, it takes a while to check it all, but it will transfer only what I've added lately.

---

### Post by FlyingIsFun1217 on 2008-02-27
Can I set a date to check for changes since?

Guess I'll just try it out ;)

FlyingIsFun1217

---

