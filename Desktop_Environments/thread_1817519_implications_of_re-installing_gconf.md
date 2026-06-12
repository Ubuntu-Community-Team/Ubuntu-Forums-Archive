---
title: "implications of re-installing gconf"
date: 2011-08-03
forum: Desktop Environments
---

### Post by me.translucent on 2011-08-03
due the issue mentioned in [http://ubuntuforums.org/showthread.php?t=1808644]("http://ubuntuforums.org/showthread.php?t=1808644")i am contemplating reinstalling gconf, how would that effect my system ?

---

### Post by jerrrys on 2011-08-04
just tried

gconftool-2 --direct \
  --config-source user-configuration-source \
  --recursive-unset

and that did nothing for me.

so i backed up .gconf and .gconfd folders in the home folder and just deleted the originals with mixed results.

first off my custom setting are now gone and most (but not all) of the default settings have
been restored.  i have some default launchers missing and really did not look much further
to see if anything else was borked.

good news is when i restored the backup files, everything went back to normal.

so to me, it looks like you can play with gconf as long as you have those files backed up

---

