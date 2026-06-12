---
title: "Sound juicer freezes while ripping mp3s"
date: 2005-12-09
forum: Desktop Environments
---

### Post by dcast on 2005-12-09
Sound Juicer freezes while ripping mp3s and when I close it it won't open up again. Why is this?

Thanks

---

### Post by aysiu on 2005-12-10
Assuming your username is dcast, try this: ```
cp /home/dcast/.gconf/apps/sound-juicer/%gconf.xml /home/dcast/.gconf/apps/sound-juicer/%gconf_backup.xml
cp /home/dcast/.sound-juicer.dcast /home/dcast/.sound-juicer.dcast_backup
cp /home/dcast/.local/share/applications/sound-juicer.desktop
 /home/dcast/.local/share/applications/sound-juicer.desktop_backup
rm /home/dcast/.gconf/apps/sound-juicer/%gconf.xml
rm /home/dcast/.sound-juicer.dcast
rm /home/dcast/.local/share/applications/sound-juicer.desktop
sound-juicer
``` Any difference?

---

### Post by dcast on 2005-12-12
Thanks aysiu i'll try that and let you know how it goes

---

### Post by aysiu on 2005-12-12
FYI:
cp means copy
rm means remove

---

### Post by dcast on 2005-12-15
Yes I knew that

---

### Post by dcast on 2005-12-15
Apparently there is no such file or directory? Could it be somewhere else or what?

---

