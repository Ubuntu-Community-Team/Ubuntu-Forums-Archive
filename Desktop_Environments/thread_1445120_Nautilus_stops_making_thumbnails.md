---
title: "Nautilus stops making thumbnails"
date: 2010-04-02
forum: Desktop Environments
---

### Post by Birion on 2010-04-02
Hi,

for some reason Nautilus (on 9.10) stopped thumbnailing any new (unthumbnailed) files. Just shows the clock icon and does nothing. The last time this happened, deleting ~/.thumbnails helped (but having to recreate the thumbnails leads to new stoppage, which leads to deleting, which...), and the size of the folder was ~75MB or similar, just like now, so I'm thinking it may have something to do with the size, but I don't see how. Does anyone know if there's a solution to this? Thanks.

---

### Post by Shazaam on 2010-04-02
Two places to look...
1. Open nautilus, go to "Edit>Preferences>Preview>Show thumbnails. Default is "Local Files Only"
2. You can check the size limit by entering this into a terminal...
```
gconf-editor
```
Find "desktop>gnome>thumbnail cache". Default max size is 512 megabytes.

---

### Post by Birion on 2010-04-02
Both are set at default - local files only in Nautilus and 512 megabytes & 180 days old in gconf.

---

