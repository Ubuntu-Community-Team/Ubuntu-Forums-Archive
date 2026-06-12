---
title: "GRUB will not load and causes restart"
date: 2010-11-30
forum: Desktop Environments
---

### Post by GottaGoMedia on 2010-11-30
All right.  I have no idea what's going on now, but I'd like to at least retrieve my data.  I have a wubi install of 10.04 and after my entire system just came to a freezing halt this afternoon, I can't make it boot.  I get passed the bios and select Ubuntu but the "loadfont" Error flashes and then the system reboots.  I had issues last week after upgrading GRUB on this wubi install.  I took the steps I found here to fix them, but uhhh...something is very wrong in my Denmark.  I just want to retrieve my data at this point.  However, windows can't see it and from a liveCD, Ubuntu can't see it either.  I'm guessing because the "partition" is within the Windows partition?  Windows boots.  How can I retrieve my data?

Thanks

---

### Post by bcbc on 2010-11-30
Get it booting:
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5) (You need to edit the grub.cfg for version 10.04.1). 

Permanent fix after following the above workaround:
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

To just get data use a tool called [ext2read]("http://ext2read.blogspot.com/") and point it at c:\ubuntu\disks\root.disk

---

