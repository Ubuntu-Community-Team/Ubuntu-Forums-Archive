---
title: "command to delete files recursively"
date: 2009-02-08
forum: General Help
---

### Post by kWahab on 2009-02-08
Hi!
Short version: 
Need terminal command to delete file "thumbs.db" from around 1000 (nested) directories on an ntfs drive.  

Detail:
I have an ntfs partition with my picture collection on it, stored in a complex directory structure. All the directories (about 1000 of them) have a thumbs.db file in them coutesy of windows.
Need a terminal command to delete them all recursively.

Tried "rm -R thumbs.db" from the top level directory, but it doesn't work.

Also tried gui method: searched for thumbs.db from Places >> Search for Files...
got all of them listed but when i select all and delete (or shift+delete) i get a message that the deleted items folder is unavailable do you want to permanently delete? for EACH file (because of NTFS?). I have better ways to wear down my mouse/keyboard so i need a command line that can do this.

Thanks

---

### Post by uberlinux on 2009-02-08
Shell scripting can take care of this.  You should be able to find all of a certain type of file using the slocate command, then pipe the output to rm.

---

### Post by uberlinux on 2009-02-08
This may work, but not willing to test on my box right now:

sudo locate Thumbs.db | xargs rm

---

### Post by ianhaycox on 2009-02-08
to verify first use:-

```

find . -type f -name thumbs.db -exec echo {} \;

```

then replace echo with rm

```

find . -type f -name thumbs.db -exec rm {} \;

```

---

### Post by handydan918 on 2009-02-08
Wildcards may help here. 
Try your command with ls rather than rm for test purposes. 
So if ```
ls *thumbs.db
``` shows the files you want to hose, you are probably ok doing [CODE]rm *thumbs.db[CODE]

---

### Post by kWahab on 2009-02-08
Thanks ianhaycox. worked like a charm.

locate/slocate complain about missing database for the NTFS partition which i just mounted. they might work but let's face it, i'm just too lazy :)

Thanks again.

---

### Post by munishvit on 2012-06-13
> **ianhaycox said:**
> to verify first use:-

```

find . -type f -name thumbs.db -exec echo {} \;

```

then replace echo with rm

```

find . -type f -name thumbs.db -exec rm {} \;

```

thanks... It was useful to me as well.

---

### Post by lisati on 2012-06-14
Nice to know that an old thread is sometimes useful. You should be aware, however, that a lot can change in 3 years.

It must be time for this old thread to go back to sleep......

---

