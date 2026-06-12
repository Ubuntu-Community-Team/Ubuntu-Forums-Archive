---
title: "Disk Cleanup after Upgrading?"
date: 2009-03-31
forum: General Help
---

### Post by paradigm2 on 2009-03-31
Hello I've used *nix off and on for about ten years.  But I have a general question regarding all of these upgrades and what happens after them. I notice that upgrades are very frequent and often quite sizable (often full rather than incremental). Are the old files automatically being deleted or are they being kept somewhere for a possible uninstall?  I'd just like to know this in case the disk space becomes an issue later on.  Thank you.

---

### Post by benreed1088 on 2009-03-31
I dont believe they do keep old files on the computer...

---

### Post by kanikilu on 2009-03-31
There are other things you can do, such as looking for and removing orphaned packages, but probably the quickest and easiest thing you can do to recover disk space from installs/upgrades is:```
sudo apt-get clean
```

See this blog for more suggestions:

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by paradigm2 on 2009-03-31
> **kanikilu said:**
> There are other things you can do, such as looking for and removing orphaned packages, but probably the quickest and easiest thing you can do to recover disk space from installs/upgrades is:```
sudo apt-get clean
```

See this blog for more suggestions:

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

Bookmarked.  Thank you. :)

---

