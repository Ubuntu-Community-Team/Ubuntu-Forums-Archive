---
title: "Disk usage analyzer"
date: 2009-05-31
forum: Desktop Environments
---

### Post by psykro on 2009-05-31
I have a small issue I am trying to understand. (running jaunty)

When I run Disk usage analyzer on my Filesystem ("/") I get the following output (screenshot attached)

It tells me that I have 63.4 GB of my 141 GB hard drive as available free space, however the folder scan tree view display shows that I have only used 28 GB of hard drive space. To my calculations that should leave about 120 GB of free space....

(Running df -h on the partition gives a similar output below)
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             142G   78G   57G  59% /

```

Am I missing something here? If the biggest folder (home folder) is only using about 24 GB of space, where is the rest?

---

### Post by Yingy on 2009-05-31
Have you done a backup on your system?  According to this posting [http://ubuntuforums.org/showthread.php?t=356872](http://ubuntuforums.org/showthread.php?t=356872) a backup will eat away at your space.  Also try using the sudo aptitude clean, have seen that numerous times on here.  And one more little thing to check, make sure your trash is empty.  Basically all the steps the post suggests.  Good Luck.

---

### Post by psykro on 2009-06-01
Thanks for the tips, now that I think about it, it might very well be backups...didn't think of that last night.

---

