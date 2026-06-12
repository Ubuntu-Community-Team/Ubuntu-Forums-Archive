---
title: "How to save the exact state of a Windows partition and later restore it with Ubuntu"
date: 2009-09-01
forum: Desktop Environments
---

### Post by baloocis on 2009-09-01
Hello All,
I think that the title pretty much says it all - I would like to save the exact state of a Windows partition with Ubuntu (to an image file perhaps) so that I could later on restore Windows to the exact state it was in when I saved it. Is this possible? And if so, how does one do it?
Thank you in advance!

edit: Geeze, I've just discovered a thread dealing with this: [http://ubuntuforums.org/showthread.php?t=360283](http://ubuntuforums.org/showthread.php?t=360283) and a wiki too: [http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)
I'm sorry. I swear I searched first, but I somehow didn't see those...

---

### Post by Lampi on 2009-09-01
use dd if=/dev/ofYourNOTmountedWindowsDevice of=fileNameOfYourImage bs=4096

sit down, have a beer or two and relax  ... it will take a while depending on the partition size

---

### Post by baloocis on 2009-09-01
Yes, that would create the image file all right (thanks for the quick reply) - but the whole process is covered up in the thread and wiki I've linked to. Somebody should probably delete this thread as it already exists and it was a mistake to open another one: I'm sorry I didn't look around careful enough.

---

