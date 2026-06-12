---
title: "Harddisk activity"
date: 2006-01-10
forum: General Help
---

### Post by calutateo on 2006-01-10
Dear all,

My harddisk is showing activity. How may I check "who", that is what process is writing to the disk?

Regards,
Carsten

---

### Post by towsonu2003 on 2006-01-10
I don't know, but check out the list of processes to see if updatedb is there ```
ps aux | grep updatedb
``` >output means it is running. that usually is 'the one' for me...

---

