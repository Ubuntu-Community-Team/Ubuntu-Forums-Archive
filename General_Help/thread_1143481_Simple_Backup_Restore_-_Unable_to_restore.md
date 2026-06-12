---
title: "Simple Backup Restore - Unable to restore"
date: 2009-04-29
forum: General Help
---

### Post by cditty on 2009-04-29
I have been backing up my data for a few weeks without any errors, but recently I needed to pull a file out of a backup.  When I select the file and tell it to restore, the file is never restored.  

All I get is a popup box that says "Restoring, this might take some time..."  I figure 8 hours might be a little too much time.

Can anyone offer any advice on this?

---

### Post by codeseer on 2009-04-30
What format is it in? Can't you just open the archive and grab it out? files.tgz?

---

### Post by cditty on 2009-04-30
When I try that, I get "Unexpected end of file" error.  Looks like the files might be corrupted.  If they are, so much for backing up for a rainy day.

---

### Post by codeseer on 2009-04-30
Looks that way. I recommend just using rsync in a shell script for backups.

---

