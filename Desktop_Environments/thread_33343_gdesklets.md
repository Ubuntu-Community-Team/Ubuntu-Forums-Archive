---
title: "gdesklets"
date: 2005-05-10
forum: Desktop Environments
---

### Post by Zelut on 2005-05-10
Has anyone got gDesklets installed on a standard ubuntu installation?  I'm trying to get it ./confingure'd but its telling me I'm missing packages,  If anyone has any detailed steps on getting everything installed that needs to be installed I'd sure appreciate it.

From screenshots that I've seen it looks really nice... I guess even a .deb would be best.  dpkg -i is much easier than manually compiling!

---

### Post by munitras on 2005-05-10
take a look at [http://www.ubuntuforums.org/showthread.php?t=31928&highlight=gdesklets](http://www.ubuntuforums.org/showthread.php?t=31928&highlight=gdesklets)

worked first time for me.

---

### Post by darkaudit on 2005-05-10
apt-get install gdesklets.

It's in the universe repository.

CAVEAT 1: gdesklets-data is obsolete. The majority of desklets in that package haven't been updated in *years*, and no longer work with the current version of gdesklets. You're better off going to [http://gdesklets.gnomedesktop.org](http://gdesklets.gnomedesktop.org) and populating your collection from there.

CAVEAT 2: The clock does not account for Daylight Savings Time. This is a known bug, and is due to be fixed in the next release. You can fix it yourself with these instructions: [http://gnomesupport.org/forums/viewtopic.php?t=9278](http://gnomesupport.org/forums/viewtopic.php?t=9278)

---

