---
title: "I want the old shutdown dialog back."
date: 2008-12-08
forum: Desktop Environments
---

### Post by The Warlock on 2008-12-08
Ah, Gnome, where each version fixes some new thing that isn't broken.

Is there any way to get the shutdown dialog box to block out background windows the way it used to (the way gksu still does)? Setting it up so that it can get lost in your other windows AND setting it up so that it has a sixty second timer is a recipe for disaster.

---

### Post by hictio on 2008-12-08
Check this threads, perhaps they might offer you some sort of compromise solution?

- [Disable 60 second shut down timer?](http://ubuntuforums.org/showthread.php?t=978289&page=3)
- [Disable power button in Xubuntu Hardy?](http://ph.ubuntuforums.com/showpost.php?p=5497088&postcount=3)
(Referenced on the above link)

---

### Post by The Warlock on 2008-12-08
I don't care about disabling the 60 second counter, I just want it to block out background windows like it used to.

---

### Post by kawaji on 2008-12-09
If you are using Compiz-Fusion, How about enabling Login/Logout plugin ?

Delete the default window matches and Enter the following line, for example.
```
class=Gnome-session & type=Dialog
```

Also, it would be better to add the above line into an entry box of "Above" window matches of Window Rule plugin.

---

### Post by explicitly ambiguous on 2009-01-20
I too would like the old dialog back.  

For me it was much more intuitive to have one button to press to shut down/suspend/logout/etc. The new dialog doesn't by default stay above my other windows (I know I can set it to be 'Above' via compiz) which seems insane to me...    Also I use many apps in fullscreen and even with the 'Above' setting enabled in compiz the shutdown dialog does not display above them!  Highly frustrating!

Does anyone know how to regress to the old dialog?  Can I port the old version of the dialog forward somehow?  Any hints would be most welcome.

---

