---
title: "Updated... firefox and opera goofy."
date: 2009-02-03
forum: General Help
---

### Post by Rickyk on 2009-02-03
Ok I updated and its been awhile since i updated last it said (78) days...
so everytime i open firefox it brings me to the "firefox has been updated" page like when u update firefox.
but it does this everytime and since i updated my bookmarks are gone and everything so idk whats going on...
its that same with opera.
and when i try and play youtube vids on firefox it plays a couple seconds then stops.
and when i try to play games like runescape (java) it has a red x in the corner.

so idk whats going on.

---

### Post by ajgreeny on 2009-02-03
Did you do a version update (eg from 8.04 - 8.10) or just update the packages etc in your version?  In either case it may be that you have a corrupted configuration of your firefox profile.  I suggest you rename your current ~/.mozilla folder in your home folder and restart FF.  It will make a new profile and .mozila folder, and you can then copy into that some of the files and folders from your old .mozilla folder, particularly the bookmarks which are now in the *places.sqlite* file, not *bookmarks.html*.  I wouild avoid using your old plugins folder as this may be the cause of your flash problems, though you could try it if you want to, and I would sugest you install flash 10, either direct from Adobe or using the ubuntu partners repository, which works brilliantly for me in 8.04.2.  I think you may need to reset your own start page from the FF Edit > Preferences dialog box.

---

