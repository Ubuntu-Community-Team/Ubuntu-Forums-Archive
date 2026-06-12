---
title: "Copying files IDE to SATA"
date: 2009-05-11
forum: General Help
---

### Post by stuboo on 2009-05-11
I've just installed 8.10 on a new machine with SATA drives.  I have an old install on an IDE drive and I want to copy some files from that drive.  When I mount the drive via USB, I don't have permission to view the files.  I know the username/pass combinations I need, but I'm not being promted for them.  How can I make this happen?

---

### Post by mb_webguy on 2009-05-11
Use this command in the terminal after you connect the drive, substituting the appropriate directory for *drive*:```
sudo chmod 777 /media/*drive*
```

---

### Post by stuboo on 2009-05-12
Thanks, mb!  Just added -R to the end of it and I'm in business.  I really appreciate it.

---

