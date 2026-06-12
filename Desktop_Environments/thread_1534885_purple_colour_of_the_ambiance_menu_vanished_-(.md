---
title: "purple colour of the ambiance menu vanished :-("
date: 2010-07-20
forum: Desktop Environments
---

### Post by AM_SOS on 2010-07-20
hi,
when i first installed 10.04 the colour of the background colour of menu shortcuts was purple. e.g. the highlighted part of the menu you get by right clicking on the desktop was purple. this was with the ambiance theme that is the set default with 10.04.
since the last few updates, i realised that this purple colour background has disappeared ! now, the background colour of the highlighted menu is off white which is the default setting of the radiance theme.
so what's happening and how do i get the purple colour again ?
thanks!

---

### Post by hansdown on 2010-07-20
Hi AM_SOS.

You didn't, by any chance, change the window buttons back to the right hand side?

Try

```
gnome-color-chooser
```

from the repos.

You can change a lot.

---

### Post by AM_SOS on 2010-07-20
hi Hansdown!
not at all. i didnt make any attempt to change the window buttons although i was aware through some post on this forum that one can do so.
i just noticed it a few days ago while checking out some 10.04 promo stuff on the internet that all the menu highlighting seemed to be purple.
it was then that i remembered that it was that way when i had first installed 10.04 on my laptop.
what do you think is happening ?
and thanks for letting me know about this nice application which allows me to tinker with the colours!

---

### Post by mcduck on 2010-07-20
The theme you saw on the promo stuff isn't the same one that is included in the final release, actually it didn't make it into the release at all..

Lucky for you, it's still available for download: [https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Dichotomy]("https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Dichotomy")

---

### Post by hansdown on 2010-07-20
You're welcome, AM_SOS. It is fun to tinker!

mcduck has a good link, for that theme.

---

### Post by AM_SOS on 2010-07-21
hi,
i am sorry. i can't seem to be find how one can download this theme.
there seem to be 6 versions at listed at the end of the page. i clicked on version 6 and got some kind of .tar package.
i then went down all the levels of this package but eventually reached some kind of coding given with a text file.
also tried to use the theme installer in the Appearances shortcut from the desktop menu. but again, haven't made any headway...
so do i download and install this theme ?
thanks!

---

### Post by mcduck on 2010-07-21
> **AM_SOS said:**
> hi,
i am sorry. i can't seem to be find how one can download this theme.
there seem to be 6 versions at listed at the end of the page. i clicked on version 6 and got some kind of .tar package.
i then went down all the levels of this package but eventually reached some kind of coding given with a text file.
also tried to use the theme installer in the Appearances shortcut from the desktop menu. but again, haven't made any headway...
so do i download and install this theme ?
thanks!

Just extract the package to ~/.themes (for your current user only) or /usr/share/themes (for all users of the system).

---

### Post by AM_SOS on 2010-07-21
sorry ! tried to extract to usr/share ...
but it says i don't have permission to extract to this directory !
???

---

### Post by mcduck on 2010-07-21
That's becasue normal user's only have write access to their own home directories. Everything esle requires root permissions. Since you aren't already familiar with the concept you should start by reading this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

(the short answer is: open a terminal and run "gksudo nautilus" to open the file manager as root. That allows you to move the theme files into /usr/share/themes/)

---

### Post by AM_SOS on 2010-07-21
thanks mcduck !
it worked like a dream :)
and i really like this theme !

---

