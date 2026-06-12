---
title: "themes"
date: 2010-12-04
forum: Desktop Environments
---

### Post by debili on 2010-12-04
hi,
i've installed maverick over an existing/broken lucid partition(with a separate /home partition), formated, and now i'm missing the original maverick theme with the 'orange' window controls..also, by applying any theme i get strange results, the scrollbar doesn't match the theme and the tabs in some applications aren't perfect.
can anybody tell me how this is possible by a fresh install ? and also how i could fix it ? thanks

---

### Post by tom4everitt on 2010-12-04
It is most likely caused by old settings in the home folder from your previous install. To see if this is the case, create a new user and see if that one faces the same problem. If it was old settings causing the problem, it should work fine for the new user. 

To clear out old Gnome settings, you can just erase them. The following files and folders in your home folder, which you will see if you choose Show hidden files in Nautilus, should be deleted:

.cache
.compiz
.gconf
.gconfd
.gnome2
.gnome2_private
.thumbnails

They will generally be recreated pretty quickly, so don't be surprised when they are not gone for long. The new ones will contain the default settings, which is the point.

---

### Post by debili on 2010-12-04
thanks; if i create a new user, everything is there, looks and works how it should. however, when i removed(not deleted) the mentioned items from my home folder, things didn't get better. first of all my internet connection sharing settings are gone (but i should have expected that) any idea where are these settings are stored? then, i still have no perfect theme, unlike by the created new user, in my account the 'old' lucid ambience theme is present instead of the mavericks one;  some themes have a question mark on their thumbnail picture, and if I pick a theme and go customizing it i notice that all the available control styles listed also are questionmarked. any ideas please?

---

### Post by tom4everitt on 2010-12-04
And what if you also remove the folder .themes? In fact, you could try removing all folders and files starting with a dot, but you would loose a lot of settings of course. Perhaps it would just be easier to start over with the new user, just moving all your files to the new users home folder (and changing auto-sign in to the new user, if you have that). 

If you kept the removed folders, you could just replace the new ones with the old ones, and you should have your internet sharing etc. as it was.

---

