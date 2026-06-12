---
title: "remove hard drive from desktop"
date: 2006-06-28
forum: Desktop Environments
---

### Post by bartbes on 2006-06-28
I love it when my desktop is clean, so I was cleaning it today and I thought it would be nicer to get rid of the 3 windows partitions on my desktop.
So after some research I thought it would help if I'd change the mount point (from /media/windows_[c,f,g] to /mnt/windows_[c,f,g] ), the drives are mounted there now, and work ok, but I still can't get the (now to nothing pointing) shortcuts off my desktop] :(

---

### Post by aysiu on 2006-06-28
Press Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volumes Visible

---

### Post by bartbes on 2006-06-28
Thanks it worked :)

---

