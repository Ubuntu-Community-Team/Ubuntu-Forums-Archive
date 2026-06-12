---
title: "Where does samba mount network drives?"
date: 2009-06-15
forum: General Help
---

### Post by berdux on 2009-06-15
hello, i am searching for about an hour now and cannot find anything.

i use samba to access my second pc's files. if i open the drive it has on top of the nautilus window a link like "smb://dragon/berdux4/". most programs when i want to go there do not understand this, ex. i want to open some mp3s on a music player or i want to mount an image inside virtualbox.

does samba mount the link somewhere i can access it normally like i do with my normal drives? (ex. /media/Berdux8 )

thanks in advance,
berdux

---

### Post by Celauran on 2009-06-15
~/.gvfs I believe. If they're both Linux machines, you'd likely do better with NFS.

---

### Post by berdux on 2009-06-15
thank you very much :)

---

