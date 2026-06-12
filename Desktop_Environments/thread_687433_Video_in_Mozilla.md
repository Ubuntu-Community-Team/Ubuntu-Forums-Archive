---
title: "Video in Mozilla"
date: 2008-02-04
forum: Desktop Environments
---

### Post by mjbardel on 2008-02-04
Just installed Unbuntu and I'm not able to see video within Mozilla. If I try and look at video on Yahoo.com and/or youtube I don't see any video. Could someone point me in the right direction to get this working?

Thanks

---

### Post by blazercist on 2008-02-04
sudo apt-get install flashplugin-nonfree

---

### Post by hollowhead on 2008-02-04
If this doesn't work (ie says it cannot install the plugin) and it has once and failed once for me see this thread 

[http://ubuntuforums.org/showthread.php?t=686624&highlight=flash](http://ubuntuforums.org/showthread.php?t=686624&highlight=flash)

create the plug ins folder and dump the flash library inti it and it will work.

---

### Post by mjbardel on 2008-02-04
Hollowhead - the link you provided was helpful , thanks. Here's what worked for me:
* disabled extensions within Mozilla.
* Uninstalled Gnash.
* Rebooted and went to a site that needed flash. Adobe flash installed right from that web page and all is working now.

---

