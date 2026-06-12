---
title: "k3b complaining about nonexistent folder"
date: 2010-08-28
forum: Desktop Environments
---

### Post by barna on 2010-08-28
Any time I start k3b, it complains about 'The file or folder /media/disk/.... does not exist' (which indeed does not exist). Where is this path stored? How can I remove it? grep -r /media/disk ~/.kde/* does not give any hit.

---

### Post by ankspo71 on 2010-08-28
Hi,
You might find it in the k3brc file located at ~/.kde/share/config/k3brc.
Hope this helps.

---

### Post by barna on 2010-08-28
Hi, thanks. But as I wrote, none of the files under ~/.kde contained /media/disk/. Also, I have removed k3brc, and the problem still persists.

---

