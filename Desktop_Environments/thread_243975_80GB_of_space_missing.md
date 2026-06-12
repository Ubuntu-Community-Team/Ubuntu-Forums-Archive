---
title: "80GB of space missing"
date: 2006-08-25
forum: Desktop Environments
---

### Post by 2frykai on 2006-08-25
Hi,

I've got a 150GB hard disk with Ubuntu and MythTV on it. The install is pretty new, so I've only got about 20GB worth of files. 

However, df says that I've used up over 100GB of space! 

Baobab reports: 
Total filesystem capacity: 143.9GB (used: 103.7GB available: 40.2GB)
Directory tree: 
     /(root) 24.4GB 100%
     ...

I've tried clearing out my Cached Package Files, but no joy. That's 80GB of unaccounted space!

Does anybody have any ideas on what could be wrong?

Thanks in advance. 
2frykai

---

### Post by quonsar on 2006-08-25
have you deleted a lot of files using sudo or su or logged in as root? if so, your deleted files are probably sitting in /root/Trash or /home/Trash-root. open a terminal and enter ```
sudo nautilus --nodesktop --browser /
``` and have a look around. i lost 10 gigs that way and once i emptied the root Trash folders it came back!

---

### Post by 2frykai on 2006-08-26
Thanks! 

Turns out another user had deleted a whole bunch of stuff, but I couldn't see those files! Running 

```
sudo baobab
```

lets me see everything!

Thanks again!
2frykai

---

