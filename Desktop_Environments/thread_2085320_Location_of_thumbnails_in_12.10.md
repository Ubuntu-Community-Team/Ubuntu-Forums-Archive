---
title: "Location of thumbnails in 12.10"
date: 2012-11-17
forum: Desktop Environments
---

### Post by Charlotte18 on 2012-11-17
After upgrade to 12.10, the .thumbnails folder in the home folder no longer appears to store the thumbnail images. Where are the thumbnail images being stored in 12.10?

---

### Post by ajgreeny on 2012-11-17
No idea, but try ```
locate thumbnails | grep $USER
``` in terminal and you should find them all.

---

### Post by Charlotte18 on 2012-11-17
Found them in the .cache folder. Thanks.

---

