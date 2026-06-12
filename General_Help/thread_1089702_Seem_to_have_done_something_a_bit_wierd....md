---
title: "Seem to have done something a bit wierd..."
date: 2009-03-07
forum: General Help
---

### Post by kneewax on 2009-03-07
OK, I've messed something up, but I am not sure how or what.

When I installed Intrepid 64bit I created 3 partitions, 1 root partition, 1 to which I moved my $home folder immediately after install and a data partition.  

Now my root partition is full!  Obviously I need to rectify this, and I can re-align my Partitions slightly - BUT would rather find out if there is anything in the root partition I can safely delete to make space.

Also I was under the impression that most programs and updates were installed in the $home folder which is on a seperate partition, so what could have caused the root partition to bloat like this?

Cheers

---

### Post by arsenic23 on 2009-03-07
Setting are in your home folder, but programs, logs, and other binaries are going to be in you / with that setup.

---

### Post by kneewax on 2009-03-07
OK, something strange is going on here, since posting this I have looked at my data partition and the used space has doubled today.  Something seems to be writing masses of data to the disk.

Now I can't log into the GUI because of space issues.

Any ideas folks?

---

### Post by arsenic23 on 2009-03-07
If you are sure the same process is filling up both partitions, then go to the root of your data path, /home/ I'm asuming, and run:
```
find -type f -cmin -30 -ls
```


You'll see all the files 30minutes or newer.  Should help give you and idea on whats filling up your drive.

---

