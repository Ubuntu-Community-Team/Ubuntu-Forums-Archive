---
title: "removing junk files"
date: 2008-12-03
forum: General Help
---

### Post by abhilashm86 on 2008-12-03
is there any procedure that removes junk files from file system which most are downloaded and other files,please tell command to remove junk files.........

---

### Post by kpkeerthi on 2008-12-03
See [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

Also look in ~/.config - This is where application-specific config files are stored (by some applications). If you no longer have the app installed you may remove the corresponding config files.

~/.thumbnails - This is where nautilus caches the thumnails (for previews). I usually keep the recently used (in the last 2 weeks) thumbails, deleting the rest.
```
find ~/.thumbnails -type f -mtime +14 -exec rm '{}' ';'
```

---

### Post by Dj Melik on 2008-12-03
Run these commands:

sudo apt-get autoremove --purge
sudo apt-get autoclean

---

