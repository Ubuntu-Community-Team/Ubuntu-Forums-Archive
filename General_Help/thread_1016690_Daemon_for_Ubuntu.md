---
title: "Daemon for Ubuntu?"
date: 2008-12-20
forum: General Help
---

### Post by lwordish on 2008-12-20
Looking for a way to have 4 .iso-files mounted at the same time. Like Daemon does in Windows. Is there such a program? Or can I do it any other way (maybe in the terminal)? I have Gmountiso installed now.

---

### Post by bluefrog on 2008-12-20
open a terminal

mkdir {1,2,3,4}
sudo mount -o loop /path/to/iso 1
and so on.

---

### Post by lovelyvik293 on 2008-12-20
Use 
```

sudo mount -o loop -t iso9660  /path/to/iso /dir/created_with_mkdir

```

---

### Post by 3rdalbum on 2008-12-20
You need a new mount point for every ISO file. A mount point is less complicated than it sounds; it's literally just a folder where you want the contents of the disc image (or disk) to appear. You generally create your mount points in /media, and you give them the same permissions that you want for the files that will appear inside.

---

