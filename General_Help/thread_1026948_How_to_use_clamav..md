---
title: "How to use clamav."
date: 2008-12-31
forum: General Help
---

### Post by jerome1232 on 2008-12-31
I currently have a headless server that torrents files for me, when torrents complete they get moved to a folder that is shared to 3 Windows computers.

I was looking to use clamav to either automatically scan that directory when a new file gets moved in or at least scan the directory on a regular interval. Is this possible with clamdscan, or would I have to create a script using clamscan and slap it into cron?

---

### Post by ju2wheels on 2008-12-31
Yes it is possible, I would use the cron route with a script that notifies you if it finds something.

Scan file/dir and output only that which is infected or nothing:
```

clamscan -i file_or_dir

```

You will find however that you will most likely need to modify the clam settings as its not configured to scan moderately sized files by default and will report some form of file too big error.

Edit: From experience I can also tell you that its accuracy in scanning .exe files should be taken with caution as ive had cases where it passed scans on both clamscan and a windows av and still managed to pop a virus during install on a windows box.

---

### Post by RealPSL on 2008-12-31
My script from /etc/cron.daily if your are interested

```

$ cat clamav
#! /bin/sh

CLAMSCAN=/usr/bin/clamscan
CLAMOPTS="-l /var/log/clamav/clamscan.log --quiet -r -i"
DIRS="/var/tmp /tmp /home /var/lib/iso/downloads"

test -x $CLAMSCAN && $CLAMSCAN $CLAMOPTS $DIRS

```

Basically scans all the locations I have write access to and writes out to the log file shown.

---

