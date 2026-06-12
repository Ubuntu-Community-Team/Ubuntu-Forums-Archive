---
title: "HELP: Restoring files from formatted ext3 to ext4"
date: 2009-05-08
forum: General Help
---

### Post by paranoid_humanoid on 2009-05-08
I've just done something really stupid. I formatted a 80 GB parition from ext3 to ext4 and installed ubuntu jaunty on it by mistake.

Is there any way I can recover any of the files on that drive? I used ubuntu's installer for the formatting.

---

### Post by piratebill on 2009-05-08
SHUTDOWN that drive!  If there is any chance data can be written to the drive, you're hosed.  

boot with a live cd (backtrack 3 would be a good choice [http://www.remote-exploit.org/backtrack_download.html](http://www.remote-exploit.org/backtrack_download.html)) and run foremost.  Foremost will only recover certain file types like photos, documents, media files, etc.  If that doesn't get everything you need back, try autopsy (also on backtrack 3).

This link might also help
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


Since you installed Jaunty on that drive, your chances are not looking very good.

---

### Post by Sef on 2009-05-08
Possibly [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), but I don't know if it will work on ext4.

---

